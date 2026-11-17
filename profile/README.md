<div align="center">

# Refactor Room

**Open-source tools for engineering with AI agents, and for checking the results.**

Revisit, reflect, and understand a little better each time. One 0.1% improvement at a time.

</div>

---

## Our projects

AI coding agents are fast. Trusting what they produce is the hard part. Our three projects work together to help with that:

| | Project | What it does | Get started |
| --- | --- | --- | --- |
| 🐼 | **[Panda Suite](https://github.com/refactorroom/panda-suite)** | 25 Agent Skills for engineering work, from requirements to release | `npx panda-suite@latest install --all` |
| 🛡️ | **[Invaris](https://github.com/refactorroom/invaris)** | Tests whether your checks catch a deliberate code change | `npx --package=invaris-cli@latest invaris check` |
| 📊 | **[Evaris](https://github.com/refactorroom/evaris)** | Evaluates agents and skills with repeatable experiments | `npx evaris-cli@latest --help` |

---

### 🐼 Panda Suite: Agent Skills for engineering work

[![Panda Suite](https://raw.githubusercontent.com/refactorroom/panda-suite/main/images/branding.png)](https://github.com/refactorroom/panda-suite)

**Think clearly. Build carefully. Ship confidently.**

Panda Suite is a set of 25 independent Agent Skills for Claude Code, OpenAI Codex, and other compatible hosts. Each skill handles one job:

- **Discover:** `panda-requirements`, `panda-brainstorm`, `panda-research`, `panda-learn`
- **Plan and build:** `panda-plan`, `panda-spec`, `panda-execute`, `panda-refactor`, `panda-setup`
- **Check:** `panda-review`, `panda-test`, `panda-debugger`, `panda-sec`, `panda-perf`, `panda-impact`
- **Ship and document:** `panda-release`, `panda-write`, `panda-manual`, `panda-git`

```sh
npx panda-suite@latest install --all                                   # every skill, into ~/.agents/skills
npx panda-suite@latest install --skill panda-plan --skill panda-review  # or just the ones you need
npx panda-suite@latest update                                          # update the installed skills later
```

Or load it as a Claude Code or Codex plugin from a clone of the repository.

Use a single skill on its own. Explaining one function doesn't need a project plan. When a task spans several steps, **Panda Lead** picks the smallest workflow that fits. The skills report what they actually verified and what they did not.

[Repository](https://github.com/refactorroom/panda-suite) · [Documentation](https://refactorroom.github.io/panda-suite/) · [Usage guide](https://github.com/refactorroom/panda-suite/blob/main/docs/usage.md) · [ภาษาไทย](https://github.com/refactorroom/panda-suite/blob/main/README.th.md)

---

### 🛡️ Invaris: check that your checks work

[![Invaris](https://raw.githubusercontent.com/refactorroom/invaris/main/assets/banners/github-readme-1600x480.png)](https://github.com/refactorroom/invaris)

A passing check tells you little if it would also pass on broken code. **Invaris** finds out. It makes a deliberate change in a temporary copy of your project, then confirms that your guards or tests fail as expected.

- **`challenge`:** add an expected violation and confirm a guard catches it, such as a forbidden import.
- **`mutate`:** change the code and see whether your tests catch it (`KILLED`) or miss it (`SURVIVED`).
- **`campaign`:** run several experiments together, with repeats, a mutation score, and an acceptance policy.
- **JSON reports** with clear exit codes for CI pipelines, scripts, and AI agents.

The Go core uses only the standard library. Builds are available for Linux and macOS, and you can also install with npm.

[Repository](https://github.com/refactorroom/invaris) · [Documentation](https://refactorroom.github.io/invaris/) · [Releases](https://github.com/refactorroom/invaris/releases)

---

### 📊 Evaris: evaluate agents and skills reproducibly

[![Evaris](https://raw.githubusercontent.com/refactorroom/evaris/main/assets/banners/github-readme-light-1600x480.svg)](https://github.com/refactorroom/evaris)

An agent saying "done" doesn't prove the task is done. **Evaris** is a Go framework for evaluating agents and skills. It runs repeatable experiments and records the evidence.

- **Blind preparation:** each case gets its own workspace and frozen inputs, and reviewer oracles stay out of the agent's workspace.
- **Deterministic grading:** results from external agent runs are graded against your own criteria. What the agent claims is treated as evidence to check, not as proof.
- **Comparisons:** compare baselines and revisions to spot regressions between skill or prompt versions.
- **Works offline, no LLM API needed.** Reports come out as JSON and Markdown. Invaris verification is optional.

[Repository](https://github.com/refactorroom/evaris) · [Workflow](https://github.com/refactorroom/evaris/blob/main/docs/workflow.md) · [Releases](https://github.com/refactorroom/evaris/releases)

---

## How they fit together

```text
   Panda Suite            Evaris                    Invaris
   ───────────            ──────                    ───────
   Skills guide    ──▶    Did the agent finish ──▶  Would your checks
   the agent              the task? (graded         catch it if it
                          experiments)              hadn't? (challenges,
                                                    mutation)
```

Each project works on its own, and they also work together. Evaris can call Invaris to verify results, and Panda Suite workflows for both are on the way.

---

## 🧪 Proof of concept

<a href="https://github.com/refactorroom/itervyn"><img src="https://raw.githubusercontent.com/refactorroom/itervyn/main/assets/banners/github-readme-1600x480.png" alt="Itervyn" width="480"></a>

**[Itervyn](https://github.com/refactorroom/itervyn)**: *Execute. Verify. Refine. Repeat.*

Itervyn is a local verification CLI for coding agents, terminal users, and CI, and the first test of how the stack fits together. It runs trusted Invaris checks and evaluates imported Evaris runs. It records one structured decision (`PASS`, `FAIL`, `INCONCLUSIVE`, or `ERROR`) and suggests a next step, such as `FIX_AND_REVERIFY`. The agent still makes the code changes and runs the fix loop. Itervyn only checks the evidence.

> Early proof of concept (v0.1.0) for Linux and macOS, pinned to specific Invaris and Evaris versions.

---

<div align="center">

It takes small, steady steps. Sometimes we read something, forget it, and come back to find it makes more sense.<br>
We hope this can be your Refactor Room, too :)

⭐ **If any of these help you, a star helps others find them.**

</div>
