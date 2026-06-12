---
title: "reduced hard drive with dual boot in wubi"
date: 2010-09-01
forum: General Help
---

### Post by laser101uk on 2010-09-01
Hi

I have ubuntu 10.4 installed in xp. Ubuntu tells me I have 50 gigs  HD space yet the folder tells me I only have 700 mgs  and i am getting a warning of not enough space on the computer. my question is .  is this due to windows claiming the space and not allowing enough to be used by ubuntu? If I delete windows and make this computer all linux will that help? 

many thanks for any ideas

---

### Post by siddharthshetty on 2010-09-01
> **laser101uk said:**
> Hi

I have ubuntu 10.4 installed in xp. Ubuntu tells me I have 50 gigs  HD space yet the folder tells me I only have 700 mgs  and i am getting a warning of not enough space on the computer. my question is .  is this due to windows claiming the space and not allowing enough to be used by ubuntu? If I delete windows and make this computer all linux will that help? 

many thanks for any ideas

You've probably given too much space to the ubuntu partition.
Even I have dual boot with xp on a 250GB hard drive.
and while using wubi to install ubuntu i installed it in the d:\ drive instead of the c:\ drive.
just see if you can access that space in ubuntu 10.04 just go to your home folder and in the bottom of the window you will see a line called free space it should mostly be the space you've lost :)

---

### Post by Mark Phelps on 2010-09-01
> **laser101uk said:**
> ... I have ubuntu 10.4 installed in xp...

Sounds like you have a Wubi-based install. This installs Ubuntu inside a large file resident in the MS Windows filesystem.

That results in two different filesystem spaces:
1) The partition itself
2) The Ubuntu-based filesystem.

When you install via Wubi, it only allocates a small space by default.  You're running out of space in THAT file, not in the surrounding partition.

---

