# Generative AI Disclosure

Using AI tools for this challenge is allowed. Be honest here — an accurate
"I used AI heavily" is worth more to us than an inaccurate "I did not".

**Did you use AI tools?** (yes / no):

**Which ones?** (e.g. ChatGPT, Claude, Copilot, Cursor): Gemini, Cursor

> If you answered **no**, write "N/A" in sections 1 and 2 and skip to
> section 3. That is a perfectly good answer.

---

## 1. Key prompts

List the main prompts you used. Paraphrasing is fine.

1. "How do I fix the apt-get package ordering and dependency issue in the proxy Dockerfile?"
2. "How can I prevent the test-runner from crashing with 502 Bad Gateway before the backend server finishes starting up?"
3. "The CI pipeline fails with permission denied on run-tests.sh, how do I fix file permissions in Git tracking?"

---

## 2. Where the AI got it wrong

Describe **one concrete case** where the AI's answer was wrong, outdated, or
sub-optimal. Cover: what it suggested, how you noticed it was wrong, and what
you did instead. 3–5 sentences.

When resolving the startup race condition (Defect 3), the AI initially suggested using `curl` inside the Docker healthcheck for the backend container. However, since the `backend` image is built on `python:3.11-alpine`, `curl` was not pre-installed, causing the healthcheck itself to fail. I noticed this by examining the Docker Compose startup logs showing that `curl` was not found. Instead of installing extra packages into the Alpine image, I updated the healthcheck command to use Python's built-in `urllib.request` module directly.

---

## 3. Anything in your submission you could not fully explain?

We would rather know. Write "nothing" if that is the case.

> Nothing.
