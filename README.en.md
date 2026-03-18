# 10 Things You Must Do When Using OpenClaw

> A practical guide based on real-world OpenClaw usage. Complete configuration templates + Skill templates, ready to copy and use.

---

## Repository Structure

```
openclaw-guide/
├── README.md                      # Chinese version
├── README.en.md                   # This file: English version
├── templates/
│   ├── soul.md.template           # Soul file template
│   ├── USER.md.template           # User profile template
│   ├── AGENTS.md.template         # Work guide template
│   ├── TOOLS.md.template          # Tools config template
│   └── HEARTBEAT.md.template      # Heartbeat tasks template
└── skills/
    ├── content-creation.md        # Content script Skill
    ├── decision-eval.md           # Business decision Skill
    ├── deep-learning.md           # Deep explainer Skill
    └── group-chat.md              # Group chat behavior Skill
```

---

## Core Concept

> Think of Claw as a new intern who just joined: smarter than you in many ways, but doesn't know who you are or what needs to be done. Your job is to tell it who you are, what to do, and where the boundaries are.

OpenClaw's configuration has six layers. Understanding this structure is the foundation of everything:

| Layer | File | Purpose | Update Frequency |
|-------|------|---------|-----------------|
| Soul | `soul.md` | Personality, values, hard limits | Rarely |
| Identity | `USER.md` | Who you are, what you want | Quarterly |
| Behavior | `AGENTS.md` | How to work | Occasionally |
| Tools | `TOOLS.md` | What tools can be used | As needed |
| Automation | `HEARTBEAT.md` | What to do proactively | After stable |
| Memory | `memory.md` | Accumulated memory from conversations | Daily |

---

## 10 Things You Must Do

### ① Write the soul file first — before anything else

**File: `soul.md`**

This is Claw's factory setting, the underlying logic for all behavior. Without this file, everything else is building on sand.

Four things you must define:
- **Personality & work style**: How it speaks, what communication rhythm you prefer
- **Value priority**: Which principle wins in a conflict (e.g. honesty > pleasing you)
- **Privacy hard limits**: Phone number, bank card, address, passwords — never share, never transmit
- **Learning & feedback loop**: How to reinforce good behavior, how to correct mistakes

📄 [View soul.md template](./templates/soul.md.template)

---

### ② Fill in USER.md: tell it who it's working for

**File: `USER.md`**

Every judgment Claw makes is based on "who am I helping." The more detail here, the more accurate its decisions.

Must include:
- Your professional background and current role
- Your top 2–3 work priorities right now
- Your communication preferences (conclusion first? bullet points?)
- Things you currently don't have resources to do (stop it from suggesting unrealistic options)

> **Common mistake**: Don't put workflow instructions in USER.md. USER.md describes "who you are." AGENTS.md describes "how it works." Keep them separate.

📄 [View USER.md template](./templates/USER.md.template)

---

### ③ Define the workflow with AGENTS.md

**File: `AGENTS.md`**

Think of this as the employee handbook. Two most critical sections:

**Standard steps when receiving a task** (prevents it from "half-understanding then starting"):
```
Step 1: Restate understanding →
Step 2: List missing info →
Step 3: Execute →
Step 4: Deliver + summary
```

**Autonomous decision boundary** (prevents it from acting on its own):
- What can it decide by itself?
- What must it ask you first?
- Who to escalate to, and how?

Without an escalation path, Claw will find a workaround and tell you after. With one, it stops and waits for you.

📄 [View AGENTS.md template](./templates/AGENTS.md.template)

---

### ④ TOOLS.md: the blocklist matters more than the allowlist

**File: `TOOLS.md`**

Many people only write "can use browser" — but forget to write "cannot log into accounts." Then Claw does things on your behalf you never knew about.

**Principle of least privilege**: Only enable tools you actually need. For each tool, define both what it CAN do and what it CANNOT do.

| Tool | Most important restriction |
|------|---------------------------|
| Browser | No login, no form submission, no registration, no posting |
| SSH | Server whitelist required; dangerous commands need confirmation |
| Voice | Show transcription first; ask before acting on ambiguous input |
| Camera | Don't activate without instruction; don't store; don't scan faces |

📄 [View TOOLS.md template](./templates/TOOLS.md.template)

---

### ⑤ After important conversations, immediately trigger a memory command

**File: `memory.md` (triggered in conversation)**

This is the most overlooked step — and the root cause of "my Claw keeps forgetting things."

When a conversation ends or the context window overflows, Claw forgets everything that wasn't explicitly stored. **Saying it doesn't mean it's saved.**

After every important decision, preference, or rule, follow up with:

```
Write the conclusions from our conversation into your memory.md.
Format: date + one-line summary + action requirement.
Tell me what you wrote when done.
```

Once this becomes a habit, Claw will keep getting to know you — instead of meeting you for the first time every session.

---

### ⑥ Turn repeated tasks into Skills

**Method: generate in conversation**

If you've taught Claw the same thing three times, it should be a Skill.

**Skill generation formula**:
```
I want to create a new Skill:
Trigger phrase: [what I say to activate it]
Input: [what I give you]
Output format: [what you produce, format requirements]
Quality standard: [what "done well" looks like]
Restrictions: [what must not appear]
```

Common scenarios worth turning into Skills: content script generation, business opportunity evaluation, file format conversion, writing in a specific style.

📄 [View ready-made Skill templates](./skills/)

---

### ⑦ Only learn Skills from official platforms

**Operating principle (no need to tell Claw)**

OpenClaw is open source, and the Skill marketplace is a wild west — just like searching for software in the early internet days and finding twenty suspicious download links.

**Only get Skills from these sources**:
- Bytedance official: [Coze Platform](https://www.coze.com)
- Tencent official: [SkillHub](https://skillhub.tencent.com) — Chinese-optimized, security-audited, fast domestic downloads
- Alibaba official: [Bailian Platform](https://bailian.aliyun.com) — integrated with Qwen models, one-click deployment
- OpenClaw official: [ClawHub](https://clawhub.ai) — original marketplace, 3,000+ Skills
- Advanced users: [awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) — GitHub, 5,400+

**Red flags for risky Skills**:
- Asks for your API Key or account password
- Vague description that doesn't clearly explain what it does
- Unknown origin, no maintainer information

---

### ⑧ Host in the cloud — don't self-host on a local machine

**Operating principle (no need to tell Claw)**

**Why cloud hosting wins**:
- Major cloud providers handle security — you don't have to be a sysadmin
- Auto-recovery when things break — no need to physically "fix the server"
- No risk of accidentally leaving data on a local machine due to poor isolation

---

### ⑨ Configure HEARTBEAT.md last — get stable first, automate after

**File: `HEARTBEAT.md`**

HEARTBEAT is what turns Claw from "only moves when you call it" to "works proactively." Delete this file and Claw becomes purely reactive.

But because it runs automatically, the risk is also highest.

**Recommended rollout order**:
```
USER.md → AGENTS.md → TOOLS.md → [run stable for 1–2 weeks] → HEARTBEAT.md
```

**Before configuring any heartbeat task, ask yourself**: if this task runs and something goes wrong, what's the consequence? For anything unacceptable, add a "notify me to confirm before executing" safeguard.

**Three types of heartbeat tasks**, from lowest to highest complexity:
1. **Scheduled tasks**: daily briefing, weekly digest
2. **Triggered tasks**: PR/sentiment alerts, deadline reminders
3. **Guardian tasks**: daily self-check, rule conflict detection

📄 [View HEARTBEAT.md template](./templates/HEARTBEAT.md.template)

---

### ⑩ Stay balanced, be patient, keep feeding data

**Mindset principle — the most important, most often ignored**

This one is for you, not for Claw.

**Avoid both extremes**:
- **Over-expecting**: thinking it can do everything the moment you install it, then spending 20 hours a day "fixing the shrimp"
- **Giving up too soon**: quitting after one or two failures and saying "this thing is useless"

Users who get great results got there because they fed data every day, corrected every mistake and made it remember, and turned every repeated scenario into a Skill — this is months of accumulation.

**Habits for continuous data feeding**:
- Important conversations, meeting recordings → summarize and feed to Claw
- Articles you've written, talks you've given → let it learn your voice and style
- Every time it does well or poorly → give immediate feedback, make it remember

> "The more data you feed it, the better it knows you. The longer you talk to Claw, the clearer your own thinking becomes."

---

## Configuration Quick Reference

| File | Required fields | Update frequency | Template |
|------|----------------|-----------------|----------|
| `soul.md` | Personality, values, privacy limits, feedback mechanism | Rarely | [→](./templates/soul.md.template) |
| `USER.md` | Professional background, current goals, communication preferences | Quarterly | [→](./templates/USER.md.template) |
| `AGENTS.md` | Task workflow, decision boundaries, escalation path | Occasionally | [→](./templates/AGENTS.md.template) |
| `TOOLS.md` | Allow/block list for each tool | As needed | [→](./templates/TOOLS.md.template) |
| `HEARTBEAT.md` | Scheduled tasks, trigger conditions, self-check rules | After stable | [→](./templates/HEARTBEAT.md.template) |

---

## About This Project

Built from real-world OpenClaw usage experience, contributed by the community.

Issues and PRs welcome — share what works for you.

---

*OpenClaw official: [openclaw.ai](https://openclaw.ai) · Skills marketplace: [ClawHub](https://clawhub.ai)*
