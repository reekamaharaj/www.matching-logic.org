# Matching Logic

**Matching Logic** is a unifying foundational logic for programming
languages, specification, verification. It serves as the foundation of
the [K framework](https://kframework.org): a formal language framework
where all programming languages must have a formal semantics and all
language tools are automatically generated by the framework from the
semantics at no additional costs, in a correct-by-construction manner.

Traditionally, concrete behaviors of programs are defined by
[operational
semantics](https://en.wikipedia.org/wiki/Operational_semantics), while
the properties of them are specified and proved using [axiomatic
semantics](https://en.wikipedia.org/wiki/Axiomatic_semantics), such as
[Hoare logic](https://en.wikipedia.org/wiki/Hoare_logic). Unfortunately,
axiomatic semantics of real languages are rather complex, so correctness
proofs are necessary in order to trust the proven properties. Moreover,
such proofs have to be maintained as the language changes, which is
generally perceived as a burden. Ideally, we would like to have only
*one* reference language semantics, which are used for both deriving
program behaviors and verifying programs.


### For programming language semanticists:

**Matching Logic** allows us to regard a programming language through both
operational and axiomatic lenses at the same time, making no distinction
between the two. The semantics of a programming language is given in
**Matching Logic** as a set of rewrite rules. Both operational behaviors and
formal properties of a program are derived using the
*language-independent* proof system of **Matching Logic**. That is, we use
the same proof system to reason about all programming languages, which
is different from the classic axiomatic semantics approach where
different languages require their own set of proof rules (see, e.g.,
[Hoare logic rules](https://en.wikipedia.org/wiki/Hoare_logic#Rules) for
a set of proof rules that were designed specifically for a simple
imperative language). In conclusion, one **Matching Logic** semantics
fulfills the roles of both operational and axiomatic semantics in a
uniform manner.

One of the key observations made by **Matching Logic** is that program
states can be represented as algebraic datatypes called
*configurations*. A configuration contains all information of the
program state, such as its current computation (i.e. the program/code),
its computing context (e.g., environments, heaps, etc.), input and
output buffer, and many others. 

Program configurations can be *matched*
by (configuration) *patterns*, which are **Matching Logic** formulas with
variables and constraints. A rewrite rule of a **Matching Logic** semantics
has the form `lhs =\> rhs` where `lhs` and `rhs` are patterns. It specifies
that all configurations matching `lhs` should rewrite to the
configurations matching `rhs`, in one computation step. In this way,
**Matching Logic** defines the formal semantics of a programming language by
defining the set of all its configurations and then defining a
[transition system](https://en.wikipedia.org/wiki/Transition_system)
over the configurations using rewrite rules.

### For logicians:

**Matching Logic** is a powerful extension of the [normal modal
logic](https://en.wikipedia.org/wiki/Normal_modal_logic) with
many-sorted universes, many-sorted modalities, First-Order Logic (FOL)
quantifiers ∀ and ∃, and the least fixpoint μ-binder. Many
logics/calculi/models, especially those important in the study of
programming languages, can be defined as theories in **Matching Logic**.
Here is a non-exhaustive list of the logics/calculi/models that are
definable in **Matching Logic**:

-   FOL and its extension with least fixpoints
-   Modal logic variants and extensions, in particular, modal μ-logic
    and hybrid logic
-   Temporal logics such as Linear Temporal Logic (LTL) and Computation
    Tree Logic (CTL)
-   Dynamic logic
-   Hoare logic, which is the foundation of most existing
    state-of-the-art program verifiers
-   Reachability logic, which is the foundation of language-independent
    program verification that is implemented by the K framework
-   Separation logic and its extension with recursive definitions
-   Equational and rewriting logic
-   Many-sorted and order-sorted algebras
-   Complex type structures such as polymorphic types, function types,
    and dependent types
-   λ-calculus
-   Pure type systems

The diagram below depicts the relationship among these
logics/calculi/models on the right. The arrows mean "is subsumed by" or "can be
defined in".
As shown, many important logical systems can be subsumed by or
defined in **Matching Logic** as its fragments and/or logical theories.

<br>

<img src="/assets/logics.png" alt="Matching Logic" width="800"/>

---

## Getting Started

**Matching Logic** is the result of a continuous 20-year effort in finding a
foundation logic for formal language frameworks,
such as [the K language framework](https:kframework.org), and has led
many research papers. 

Here, we select
some milestone papers for starters, discuss the ongoing projects and
open problems, and review some earlier papers that compare **Matching Logic** with the classic Hoare-style program verification.

### Publications

<details open>
    <summary>Core publications</summary>
    
| Author/Contributors  |  Title & Link | Journal |Date Published |
| ------------- | ------------- | ------------- | ------------- |
| **Grigore Rosu** |  [Matching Logic](https://fsl.cs.illinois.edu/publications/rosu-2017-lmcs.html)[^1]  | LMCS  |2017  |
| **Xiaohong Chen, Grigore Rosu** |  [Matching mu-Logic](https://fsl.cs.illinois.edu/publications/chen-rosu-2019-lics.html)[^2] | LICS |2019 |

</details>

[^1]: This paper is a comprehensive in-depth survey paper of the mathematical
    foundations of matching logic. The paper discusses the motivation of
    matching logic and its usage in the [K framework](https://kframework.org),
    defines its syntax and semantics,
    shows that many logics can be defined as theories, including FOL,
    modal logic S5, and separation logic, and proposes a sound and
    complete proof system for theories that feature equality.

[^2]: This paper is the canonical paper that proposes matching logic in its full
    generality. It adds fixpoints to matching logic, as suggested by its name:
    matching mu-logic, where "mu" is the operation that builds least fixpoints, as in
    [modal mu-calculus](https://en.wikipedia.org/wiki/Modal_%CE%BC-calculus).
    To keep the name simple and consistent, we drop the "mu" and simply call it "matching logic"
    in our current and future papers.
    This paper discusses more logics that can be defined in matching logic,
    including FOL with least fixpoints, modal μ-logic, temporal logics, dynamic logic,
    separation logic with recursive definitions, and reachability logic (i.e., program verification).
    One of the main contributions of the paper is the proposal of a new proof system for matching logic
    that supports formal reasoning in all theories, and thus addressing
    the limitation of the previous LMCS'17 proof system that it only works for equality-featuring theories.
    The new proof system now serves as the foundation for formal reasoning in the K framework
    and is used as a basis for generating machine-checkable correctness certificates for all K tools.

<details open>
    <summary>Other publications</summary>
    
| Author/Contributors  |  Title & Link | Journal |Date Published |
| ------------- | ------------- | ------------- | ------------- |
| **Zhengyao Lin, Xiaohong Chen, Minh-Thai Trinh, John Wang, Grigore Rosu** |  [Generating Proof Certificates for a Language-Agnostic Deductive Program Verifier](https://fsl.cs.illinois.edu/publications/lin-chen-trinh-wang-rosu-2023-oopsla.html)[^3]  | OOPSLA  |2023  |
| **Adam Fiedler** |  [Deduction in Matching Logic](https://is.muni.cz/th/mcbtk/?lang=en)[^4] | Master's Thesis |2022 |
|**Xiaohong Chen, Zhengyao Lin, Minh-Thai Trinh, Grigore Rosu**|  [Towards a Trustworthy Semantics-Based Language Framework via Proof Generation](https://fsl.cs.illinois.edu/publications/chen-lin-trinh-rosu-2021-cav.html)[^5] | CAV |2021 |
|**Xiaohong Chen, Minh-Thai Trinh, Nishant Rodrigues, Lucas Pena, Grigore Rosu** | [Towards A Unified Proof Framework for Automated Fixpoint Reasoning Using Matching Logic](https://fsl.cs.illinois.edu/publications/chen-pena-rodrigues-rosu-trinh-2020-oopsla.html)[^6] | OOPSLA|2020 |
|**Xiaohong Chen, Grigore Rosu**|  [A General Approach to Define Binders Using Matching Logic](https://fsl.cs.illinois.edu/publications/chen-rosu-2020-icfp.html)[^7] | ICFP|2020 |
|**Xiaohong Chen, Dorel Lucanu, Grigore Rosu**|  [Initial Algebra Semantics in Matching Logic](https://fsl.cs.illinois.edu/publications/chen-lucanu-rosu-2020-tr.html)[^8] | Technical Report|2020 |
|**Xiaohong Chen, Dorel Lucanu, Grigore Rosu**| [Matching Logic Explained](https://fsl.cs.illinois.edu/publications/chen-lucanu-rosu-2020-trb.html)[^9]| JLAMP|2020 |

</details>

[^3]: A language-agnostic program verifier takes as input both a program with its formal specification and the formal semantics of the programming language in which the program is written, and then uses a language-agnostic verification algorithm to prove the program correct with respect to its specification, using directly the formal language semantics. Such a complex verifier can easily have bugs. This paper proposes a method to certify the correctness of each successful verification run by generating a proof certificate for it. The proof certificate can be checked by a small proof checker. The preliminary experiments apply the method to generate proof certificates for the verification of an imperative language, a functional language, and a virtual machine language, showing that the proposed method is language-agnostic.
[^4]: Matching logic (ML) is a logic designed for reasoning about programs by means of operational semantics. We investigate the foundations of matching logic and its proof systems suited for formal verification. We focus on System H, which is complete w.r.t. most matching logic theories used in practice. A problem open for several years is whether System H is complete w.r.t. all theories. In this thesis, we identify a tractable if-and-only-if-condition for completeness of System H and exploit it to find new classes of complete theories. While solving the completeness problem, we review some existing results and answer related questions on expressiveness, consistency, and (un)satisfiability. For example, we show a detailed embedding of first-order logic in matching logic, prove the well-known compactness property for ML, and present a new technique of constructing canonical models for matching logic theories with equality. We also borrow some notions from first-order logic and study their properties in matching logic.
[^5]: We pursue the vision of an ideal language framework, where programming language designers only need to define the formal syntax and semantics of their languages, and all language tools are automatically generated by the framework. Due to the complexity of such a language framework, it is a big challenge to ensure its trustworthiness and to establish the correctness of the autogenerated language tools. In this paper, we propose an innovative approach based on proof generation. The key idea is to generate proof objects as correctness certificates for each individual task that the language tools conduct, on a case-by-case basis, and use a trustworthy proof checker to check the proof objects. This way, we avoid formally verifying the entire framework, which is practically impossible, and thus can make the language framework both practical and trustworthy. As a first step, we formalize program execution as mathematical proofs and generate their complete proof objects. The experimental result shows that the performance of our proof object generation and proof checking is very promising.
[^6]: Automation of fixpoint reasoning has been extensively studied for various mathematical structures, logical formalisms, and computational domains, resulting in specialized fixpoint provers for heaps, for streams, for term algebras, for temporal properties, for program correctness, and for many other formal systems and inductive and coinductive properties. However, in spite of great theoretical and practical interest, there is no unified framework for automated fixpoint reasoning. Although several attempts have been made, there is no evidence that such a unified framework is possible, or practical. In this paper, we propose a candidate based on matching logic, a formalism recently shown to theoretically unify the above mentioned formal systems. Unfortunately, the (Knaster-Tarski) proof rule of matching logic, which enables inductive reasoning, is not syntax-driven. Worse, it can be applied at any step during a proof, making automation seem hopeless. Inspired by recent advances in automation of inductive proofs in separation logic, we propose an alternative proof system for matching logic, which is amenable for automation. We then discuss our implementation of it, which although not superior to specialized state-of-the-art automated provers for specific domains, we believe brings some evidence and hope that a unified framework for automated reasoning is not out of reach.
[^7]: We propose a novel definition of binders using matching logic, where the binding behavior of object-level binders is directly inherited from the built-in exists binder of matching logic. We show that the behavior of binders in various logical systems such as lambda-calculus, System F, pi-calculus, pure type systems, can be axiomatically defined in matching logic as notations and logical theories. We show the correctness of our definitions by proving conservative extension theorems, which state that a sequent/judgment is provable in the original system if and only if it is provable in matching logic, in the corresponding theory. Our matching logic definition of binders also yields models to all binders, which are deductively complete with respect to formal reasoning in the original systems. For lambda-calculus, we further show that the yielded models are representationally complete, a desired property that is not enjoyed by many existing lambda-calculus semantics. This work is part of a larger effort to develop a logical foundation for the programming language semantics framework K (http://kframework.org).
[^8]: Matching logic is a unifying foundational logic for defining formal programming language semantics, which adopts a minimalist design with few primitive constructs that are enough to express all properties within a variety of logical systems, including FOL, separation logic, (dependent) type systems, modal mu-logic, and more. In this paper, we consider initial algebra semantics and show how to capture it by matching logic specifications. Formally, given an algebraic specification E that defines a set of sorts (of data) and a set of operations whose behaviors are defined by a set of equational axioms, we define a corresponding matching logic specification, denoted INITIALALGEBRA(E), whose models are exactly the initial algebras of E. Thus, we reduce initial E-algebra semantics to the matching logic specifications INITIALALGEBRA(E), and reduce extrinsic initial E-algebra reasoning, which includes inductive reasoning, to generic, intrinsic matching logic reasoning.
[^9]: Matching logic was recently proposed as a unifying logic for specifying and reasoning about static structure and dynamic behavior of programs. In matching logic, patterns and specifications are used to uniformly represent mathematical domains (such as numbers and Boolean values), datatypes, and transition systems, whose properties can be reasoned about using one fixed matching logic proof system. In this paper we give a tutorial to matching logic. We use a suite of examples to explain the basic concepts of matching logic and show how to capture many important mathematical domains, datatypes, and transition systems using patterns and specifications. We put special emphasis on the general principles of induction and coinduction in matching logic and show how to do inductive and coinductive reasoning about datatypes and codatatypes. To encourage the development of the future tools for matching logic, we propose and use throughout the paper a human-readable formal syntax to write specifications in a modular and compact way.

To understand how **Matching Logic** powers
**formal program verification *for all languages***, read the following publications, where we compare
our approach to program verification with the traditional Hoare-style
verification approach:
<details open>
    <summary>Core publications</summary>
    
| Author/Contributors  |  Title & Link | Journal |Date Published |
| ------------- | ------------- | ------------- | ------------- |
|**Xiaohong Chen, Grigore Rosu**|[A Language-Independent Program Verification Framework](https://fsl.cs.illinois.edu/publications/chen-rosu-2018-isola.html) [^10]| ISoLA| 2018|
|**Xiaohong Chen, Daejun Park, Grigore Rosu**|[A Language-Independent Approach to Smart Contract Verification](https://fsl.cs.illinois.edu/publications/chen-park-rosu-2018-isola.html)[^11]| ISoLA | 2018|
|**Andrei Stefanescu, Stefan Ciobaca, Radu Mereuta, Brandon Moore, Traian Florin Serbanuta, Grigore Rosu**|[All-Path Reachability Logic](https://fsl.cs.illinois.edu/publications/stefanescu-ciobaca-mereuta-moore-serbanuta-rosu-2014-rta.html)[^12]|RTA| 2014|
|**Grigore Rosu, Andrei Stefanescu, Stefan Ciobaca, Brandon Moore**|[One-Path Reachability Logic](https://fsl.cs.illinois.edu/publications/rosu-stefanescu-ciobaca-moore-2013-lics.html)[^13]|LICS| 2013|
|**Grigore Rosu, Andrei Stefanescu**|[From Hoare Logic to Matching Logic Reachability](https://fsl.cs.illinois.edu/publications/rosu-stefanescu-2012-fm.html)[^14]|FM|2012|
|**Grigore Rosu, Andrei Stefanescu**|[Checking Reachability using Matching Logic](https://fsl.cs.illinois.edu/publications/rosu-stefanescu-2012-oopsla.html)[^15]|OOPSLA|2012|

</details>

[^10]: This invited paper describes an approach to language-independent deductive verification using the K semantics framework, in which an operational semantics of a language is defined and a program verifier together with other language tools are generated automatically, correct-by-construction.
[^11]: This invited paper reports the current progress of smart contract verification with the K framework in a language-independent style.
[^12]: This paper presents a language-independent proof system for reachability properties of programs written in non-deterministic (e.g. concurrent) languages, referred to as *all-path reachability logic*. It derives partial-correctness properties with all-path semantics (a state satisfying a given precondition reaches states satisfying a given postcondition on all terminating execution paths). The proof system takes as axioms any unconditional operational semantics, and is sound (partially correct) and (relatively) complete, independent of the object language; the soundness has also been mechanized (Coq). This approach is implemented in a tool for semantics-based verification as part of the K framework.
[^13]: This paper introduces *reachability logic*, a language-independent proof system for program verification, which takes an operational semantics as axioms and derives *reachability rules*, which generalize Hoare triples. This system improves on previous work by allowing operational semantics given with *conditional* rewrite rules, which are known to support all major styles of operational semantics. In particular, Kahn's big-step and Plotkin's small-step semantic styles are newly supported. The reachability logic proof system is shown sound (i.e., partially correct) and (relatively) complete. Reachability logic thus eliminates the need to independently define an axiomatic and an operational semantics for each language, and the non-negligible effort to prove the former sound and complete w.r.t. the latter. The soundness result has also been formalized in Coq, allowing reachability logic derivations to serve as formal proof certificates that rely only on the operational semantics.
[^14]: Matching logic reachability has been recently proposed as an alternative program verification approach. Unlike Hoare logic, where one defines a language-specific proof system that needs to be proved sound for each language separately, matching logic reachability provides a *language-independent* and *sound* proof system that directly uses the trusted operational semantics of the language as axioms. Matching logic reachability thus has a clear practical advantage: it eliminates the need for an additional semantics of the same language in order to reason about programs, and implicitly eliminates the need for tedious soundness proofs. What is not clear, however, is whether matching logic reachability is as powerful as Hoare logic. This paper introduces a technique to mechanically translate Hoare logic proof derivations into equivalent matching logic reachability proof derivations. The presented technique has two consequences: first, it suggests that matching logic reachability has no theoretical limitation over Hoare logic; and second, it provides a new approach to prove Hoare logics sound.
[^15]: This paper presents a verification framework that is parametric in a (trusted) operational semantics of some programming language. The underlying proof system is language-independent and consists of eight proof rules. The proof system is proved partially correct and relatively complete (with respect to the programming language configuration model). To show its practicality, the generic framework is instantiated with a fragment of C and evaluated with encouraging results.

## Related Links

- The [K framework](https://kframework.org) homepage.