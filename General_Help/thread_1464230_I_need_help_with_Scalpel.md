---
title: "I need help with Scalpel"
date: 2010-04-27
forum: General Help
---

### Post by houshdaran on 2010-04-27
please help

I just type this:
> sudo scalpel /dev/sda2 -o /media/m
and got this error> :
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.
[COLOR=Red]ERROR: You have attempted to use a non-empty output directory. In order
       to maintain forensic soundness, this is not allowe[/COLOR]d

---

### Post by houshdaran on 2010-04-27
hi.
please help

I just type this:
> sudo scalpel /dev/sda2 -o /media/m
and got this error> :
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.
[COLOR=Red]ERROR: You have attempted to use a non-empty output directory. In order
       to maintain forensic soundness, this is not allowe[/COLOR]d

Please also tell me how to "foremost".I also get such an error when foremost.I need some deleted files

---

### Post by cariboo on 2010-04-27
Moved to General Help, as the Cafe is not a support forum.

---

### Post by MelDJ on 2010-04-28
edit

---

### Post by zircon214 on 2010-04-28
> ERROR: You have attempted to use a non-empty output directory.That means you need to create a new, empty directory for the program to output to.

mkdir /media/m/out
                             sudo scalpel /dev/sda2 -o /media/m/out

---

### Post by lisati on 2010-04-28
Thread moved to "General Help"

---

### Post by cariboo on 2010-04-28
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by houshdaran on 2010-04-29
> **MelDJ said:**
> edit
How?

---

