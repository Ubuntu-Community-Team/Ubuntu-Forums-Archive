---
title: "VT100 Emulated Left Arrow Key Suppressed"
date: 2010-02-23
forum: General Help
---

### Post by cmnorton on 2010-02-23
I have a Linux terminal emulator running on Ubuntu 9.10 and Kubuntu 8.04. The emulator version is the same on both systems. When logging in TERMCAP is set to the same file. It's a saved termcap file that has worked across versions of Red Hat and Ubuntu, and allows me not to alter the installed TERMCAP.

If I start the emulator on the 8.04 Kubuntu system, the left arrow key works. If I start the emulator on the 9.10 Ubuntu system, the left arrow key does not work. 

What should I be looking at to fix this?

---

### Post by itcotbtoemik on 2010-03-24
Most applications on Ubuntu would be using terminfo rather than
termcap.  (It's unclear which terminal emulator you're referring
to).

---

### Post by cmnorton on 2010-03-25
> **itcotbtoemik said:**
> Most applications on Ubuntu would be using terminfo rather than
termcap.  (It's unclear which terminal emulator you're referring
to).

For Ubuntu, then, I'll try pointing to terminfo.

---

