---
title: "sound wont work"
date: 2010-04-24
forum: General Help
---

### Post by hungerformore on 2010-04-24
i just installed ubuntu 9.10 and my sound is not working what should i do

---

### Post by lyall on 2010-04-24
see LordRaiden thread in Multimedia & Video in Sticky Threads
Comprehensive Sound Problem Solutions Guide

it should help

good luck and have fun learning

---

### Post by mikewhatever on 2010-04-24
1. Make sure it's not muted.

2. Type a few more lines about your computer. Knowing the sound card model would be nice.

---

### Post by lidex on 2010-04-24
First go here and work through the entire page to fix any known karmic audio bugs:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Still no sound? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

