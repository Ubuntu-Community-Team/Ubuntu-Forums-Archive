---
title: "Question about wine and network worms"
date: 2012-09-10
forum: General Help
---

### Post by aligator12 on 2012-09-10
Hi, I connect to various wifis around town. And some of them I am sure have laptops with worms/malware. If I install wine, could a worm infect wine like it would windows? Or does wine ONLY execute things I tell it to?

---

### Post by mcduck on 2012-09-10
THe worm could (at least in theory)affect any program you are currently running i Wine (for example if you run a web browser withy Wine, the browser will have the pretty much the same vulneranbilities as the same browser runningh natively on Windows would have. Any infections, however, would be restricted to Wine's own files and it's virtual "C: drive".

However just having Wine installed will not allow any worms or viruses to work, they'd have to be specifically made to work on Linux and to execute stuff using Wine, and of course to overcome any security features of the Linux system itself before being able to do anything else.

---

### Post by aligator12 on 2012-09-10
> **mcduck said:**
> THe worm could (at least in theory)affect any program you are currently running i Wine (for example if you run a web browser withy Wine, the browser will have the pretty much the same vulneranbilities as the same browser runningh natively on Windows would have. Any infections, however, would be restricted to Wine's own files and it's virtual "C: drive".

However just having Wine installed will not allow any worms or viruses to work, they'd have to be specifically made to work on Linux and to execute stuff using Wine, and of course to overcome any security features of the Linux system itself before being able to do anything else.
Well how could I change it so that I only I can execute code?

---

