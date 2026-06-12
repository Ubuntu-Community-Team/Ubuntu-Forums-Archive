---
title: "Performance slows down after 2-3 days"
date: 2010-07-07
forum: General Help
---

### Post by bredstein on 2010-07-07
Hello!

I hope somebody has a solution to this annoying situation: right after restart my system is very fast (at least for me), but after few days it slows down to the point when using it becomes a waste of time. As soon as I restart everything is OK. Usually I keep open 1-2 Open Office files, couple large PDFs, and some Firefox tabs at the same time, nothing special. No gaming/video on this rig, just basic internet and text processing. Here are my specs:
     9.10 Karmic
     Kernel Linux 2.6.31-22-generic
     GNOME 2.28.1
     Memory: 433.1 MiB
     Processor: AMD Athlon 64 3200+
Am I wrong thinking that I have enough juice to keep these windows open? Maybe there is a way to tweak something? Many thanks for any ideas!
- Andrey

---

### Post by Johnny B on 2010-07-07
run the command 'top' in terminal to see whats using your memory/cpu.

---

### Post by mike555 on 2010-07-07
I would recommend more memory ... also make sure your swap file is big enough ..

 also setting Open Office to have 20 undos instead of 100 might help ... in open office click on tools, options, memory.

---

### Post by bredstein on 2010-07-18
> **Johnny B said:**
> run the command 'top' in terminal to see whats using your memory/cpu.
'top' reports two users (root and myself),  most of the memory (23%) is taken by XORG, the one used by the root.

---

### Post by etdsbastar on 2010-07-19
> **mike555 said:**
> I would recommend more memory ... also make sure your swap file is big enough ..

 also setting Open Office to have 20 undos instead of 100 might help ... in open office click on tools, options, memory.

Everything on ubuntu uses swap space very much, may be your swap file is very small though to handle the situations running around your desktop and your machine.

Please give us the screenshot of System -> Administration -> System Monitor

Then press the "Resources Tab" and then take a screenshot of the window and display it here, so that we can support you in a better way.

---

