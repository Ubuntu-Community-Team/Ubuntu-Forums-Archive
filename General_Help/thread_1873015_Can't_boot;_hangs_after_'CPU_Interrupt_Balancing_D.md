---
title: "Can't boot; hangs after 'CPU Interrupt Balancing Daemon' fails"
date: 2011-10-31
forum: General Help
---

### Post by FerretWithASpork on 2011-10-31
**SOLVED**

I just formatted an old desktop with Xubuntu 11.10 and everything seemed to go fine during the installation but I can't get it to boot up.
Here's the boot screen it's sticking on: [[Link]]("http://i.imgur.com/eZrcw.jpg")

I'm getting a "fail" on (from top to bottom):
[LIST]
[*]Starting restore sound card(s') mixer state(s)
[/LIST]
Don't really care about this one. I don't have a sound card in, and I'm not going to be outputting any sound from this machine.
[LIST]
[*]Starting automatic crash report generation
[*]Starting CPU interrupts balancing daemon
[/LIST]


After the CPU interrupts daemon fails it loads the LightDM Display Manager then hangs.

Any thoughts?


**SOLVED**
I didn't have a power cable plugged into the graphics card... OOPS!

---

