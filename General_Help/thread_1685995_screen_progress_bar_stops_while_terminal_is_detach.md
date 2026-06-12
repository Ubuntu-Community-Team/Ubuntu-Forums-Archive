---
title: "screen: progress bar stops while terminal is detached"
date: 2011-02-11
forum: General Help
---

### Post by Lampi on 2011-02-11
Hello screen users

How should I start the screen terminal, when my app inside this terminal will write a progress bar (percentage of completion, uptime running) to stdout in a two second interval? 

I realize the progress bar gets disjointed when I detach of screen: Once I reattach to the terminal the progress bar resumes at the value where I quit, not where it's expected to be by now.

Outside of screen I confirmed my app is still running using the top command: I can see the running time increasing, cpu usage changing, so this task is up and alive even with the detached screen terminal.

Anyone here with ideas how to cope with that??

---

