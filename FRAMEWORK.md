# Repo Therapy — Conceptual Framework

A document that captures the *why* and *what* behind the repo therapy practice.
This is not a how-to guide, a prompt template, or a list of checks to run.
It is the conceptual foundation from which any faithful implementation of
repo therapy should be derivable.

---

## What Repo Therapy Is

Repo therapy is a **structured, corrective practice** applied to a software
codebase. Its purpose is to surface what is genuinely unhealthy in a codebase
and then actively work to correct it — not as a passive audit that produces a
report, but as a hands-on collaborative engagement that leaves the codebase
in better health than it was found.

The word *therapy* is intentional. Like therapy in the human context, the
practice is:

- **Holistic** — it looks at the whole before focusing on parts
- **Prioritized by severity** — not everything that could be fixed should
  be fixed first; the practice makes a judgment about what matters most
- **Honest without being brutal** — it acknowledges what is working as
  clearly as it names what is not
- **Corrective** — diagnosis is the prerequisite, not the product. The
  therapist doesn't deliver a report and leave; they help make the adjustment.
- **Collaborative** — the human team remains the authority. The therapist
  works *with* them, not *on their behalf without them*.
- **Bounded** — a session has a defined scope and a clear endpoint

The analogy is closer to a **chiropractor** than to a talking therapist. The
chiropractor assesses, identifies the misalignment, and then — with the
patient present and consenting — makes the adjustment. The patient leaves
in better shape. No report is handed over. The work is done.

---

## What Repo Therapy Is Not

Understanding the boundaries of the practice is as important as understanding
its purpose.

**It is not a linter.**
A linter applies a fixed ruleset mechanically to every file. Repo therapy
exercises judgment about which issues matter in this specific codebase, at
this specific moment, given this specific level of maturity.

**It is not a code review.**
A code review evaluates a proposed change against the existing codebase.
Repo therapy evaluates the existing codebase against a theory of health.
There is no change being proposed — there is a state being assessed and
then actively improved.

**It is not an audit.**
An audit checks for compliance against an external standard. Repo therapy
is interested in internal coherence — does this codebase make sense on its
own terms? — and then corrects where it does not.

**It is not a replacement for deep expertise.**
Repo therapy is a structured entry into a codebase. It is designed to surface
real signal quickly and act on it. It is not a substitute for extended
familiarity with the codebase, the team, or the product domain.

---

## The Theory of Codebase Health

Repo therapy is built on a specific model of what codebase health means.
This model has a hierarchy — not because lower concerns are unimportant,
but because foundational concerns must be addressed before higher-order
concerns can be properly evaluated.

### The Health Hierarchy

**1. Structural Integrity**
Can the codebase be built, run, and tested reliably? This is the floor.
A codebase that cannot be reliably executed cannot be meaningfully evaluated
for anything else. Broken builds, missing dependencies, non-deterministic
test failures — these are not code quality issues. They are existence issues.

**2. Architectural Coherence**
Does the codebase have a recognizable structure, and does the code respect
it? Architecture is the codebase's theory of itself — the implicit or explicit
model of how responsibilities are divided. A coherent codebase is one where
a new developer can form a correct mental model of how things fit together.
An incoherent codebase is one where that model is wrong no matter how long
you look.

**3. Consistency of Practice**
Does the codebase apply its own patterns uniformly? Every non-trivial codebase
develops conventions — naming, structure, data flow, error handling. Health
at this level means those conventions are applied consistently enough that
violations are meaningful signals, not noise. Inconsistency is expensive:
it multiplies cognitive load by making every familiar pattern untrustworthy.

**4. Coupling and Dependency Health**
Are the dependencies between modules, components, and layers appropriate?
Tight coupling makes change expensive. Hidden dependencies make change
dangerous. A healthy codebase has dependencies that are explicit, directional,
and proportionate to the actual relationships between things.

**5. Signal Clarity**
Can a reader of the code understand what it is doing, and why? This is
distinct from documentation. Signal clarity means that the code itself
communicates intent — that naming, structure, and organization reduce the
gap between what the code does and what it means. A codebase with poor
signal clarity is not necessarily buggy — it is expensive to maintain
because every change requires an archaeology project.

**Why this ordering matters**

The hierarchy is not a checklist — it is a reasoning tool. Diagnosing
consistency problems in a codebase with broken architecture is premature:
you may be observing symptoms of the architectural problem, not independent
issues. Diagnosing coupling problems in a codebase that cannot build is
academic. The hierarchy prevents the therapy session from producing an
impressive-sounding list of issues that misses what actually needs attention.

It also governs the order of correction: the most foundational problems
are fixed first.

---

## The Practitioner's Role

The repo therapist is a **skilled generalist with a structured methodology
and a corrective mandate**.

**Skilled** — because the practice requires judgment. The methodology prevents
important things from being missed, but it cannot replace the capacity to
recognize what is significant versus merely imperfect.

**Generalist** — because the practice must be applicable across different
languages, frameworks, domains, and team sizes. A practice that only works
for React applications, or only for mature codebases, is not repo therapy —
it is a specialized review.

**Structured** — because the value of the practice comes partly from its
consistency. Two therapy sessions on different codebases should be
recognizably similar in form, even if their findings are completely different.

**Corrective** — the therapist does not stop at naming the problem. Once
the diagnosis is made, the therapist actively works to fix it. The session
produces a healthier codebase, not a document describing an unhealthy one.

The human team remains the authority at every step. The therapist works
transparently — naming what they see, proposing what they intend to change,
and making corrections that the human can review, guide, and override.
But the default posture is to *do the work*, not to hand it back.

The therapist's posture is **curious, honest, and hands-on**. The goal
is to understand the codebase as it is and then help it become what it
intends to be.

---

## The Session Structure

A repo therapy session has a beginning, a middle, and an end. This structure
is not arbitrary — it reflects the order in which reliable observations
can be made and meaningful corrections can be applied.

### Beginning: Orientation

Before evaluating anything, the therapist establishes a picture of what
the codebase is and what it is trying to do. This means understanding the
domain, the technology choices, the approximate scale, and any immediately
apparent context (team size, age of codebase, stated purpose).

Without orientation, evaluation is premature. A pattern that is wrong in
one context is correct in another. An architecture that is over-engineered
for one scale is appropriate for another.

### Middle: Diagnostic Traversal

The therapist moves through the health hierarchy systematically, starting
at the foundation. Each level is assessed before moving to the next. Findings
at each level are noted but not immediately acted on — the goal during
traversal is to form a complete picture before prioritizing corrections.

The traversal is top-down: structure → architecture → consistency → coupling
→ signal. It does not follow the directory structure of the codebase —
it follows the diagnostic framework.

### End: Synthesis and Correction

The therapist produces a synthesis: a prioritized account of what was found,
organized by significance rather than by the order it was discovered.

The synthesis is structured as:
- What is working well (honest acknowledgment, not reassurance)
- The primary findings (3–5 things, prioritized by the health hierarchy)
- The proposed corrections, in order of priority

Following the synthesis, the therapist moves through the corrections
collaboratively with the human team — making the changes, confirming
as they go, and leaving the codebase in better health than it was found.

The session is complete when the corrections are done, not when the
diagnosis is delivered.

---

## Quality Criteria for a Therapy Session

A well-executed repo therapy session meets the following criteria:

**Honesty** — it says what is actually true about the codebase, including
things that are uncomfortable or that reflect poorly on past decisions.

**Proportionality** — the severity assigned to each finding is proportionate
to its actual impact on developer productivity, system reliability, or
future maintainability.

**Specificity** — findings are grounded in concrete examples from the
codebase, not vague generalizations. "The codebase has coupling issues"
is not a finding. "Module A directly imports from Module C, bypassing the
abstraction boundary established in Module B" is a finding.

**Completeness at each level** — the session does not skip levels in the
hierarchy because they appear healthy. Confirming health is a finding too.

**Effectiveness** — the corrections made during the session should leave
the codebase measurably healthier at the identified priority points. A
session that produces an excellent diagnosis but makes no meaningful
improvement has not met the standard of the practice.

---

*Last updated: 2026-03-01*
