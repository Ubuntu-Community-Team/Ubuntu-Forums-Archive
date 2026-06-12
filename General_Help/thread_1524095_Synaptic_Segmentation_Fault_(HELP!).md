---
title: "Synaptic Segmentation Fault (HELP!)"
date: 2010-07-04
forum: General Help
---

### Post by JohnHeikkila on 2010-07-04
Hey,
I've been looking for an answer for this around all forums, but nothing works.
So far, I've tried:
Editing "/etc/apt/apt.conf.d/70debconf" and adding ```
APT::Cache-Limit "33554432";
```
Then I've tried
```
rm /var/cache/apt/*.bin
```
and
```
sudo rm /var/lib/apt/lists/* -f
```
Plus, I've tried reinstalling Synaptic.
No chance, doesn't work.

I've got a AMD64 running a 32-bit Kubuntu 10.04, 4GB RAM memory.
If you need any info or stats, just ask.
I really need some help here, nobody knows how to solve this and no solutions I've found work!

---

### Post by JohnHeikkila on 2010-07-04
Bump :-(

---

### Post by Chame_Wizard on 2010-07-04
Why the heck do you use Synaptic?you know Kpackagekit is the front-end package manager in KSC?
Otherwise you have to install the necessary libs.

---

### Post by JohnHeikkila on 2010-07-04
Because Synaptic allows me to reinstall, remove completely, and I just like it otherwise...

---

