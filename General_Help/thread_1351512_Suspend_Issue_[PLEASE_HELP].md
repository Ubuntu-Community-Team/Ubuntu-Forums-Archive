---
title: "Suspend Issue [PLEASE HELP]"
date: 2009-12-10
forum: General Help
---

### Post by vmanisme on 2009-12-10
I've been trying to switch over to Linux from Windows for about 2 years now and now I'm only down to 1 problem that's preventing me from using Linux 24/7.  On all previous versions of Ubuntu suspend and hibernate did not work for me at all (it would just give me a flashing cursor), now with 9.10 hibernate works and suspend kinda works.  

**The Problem:**
When I suspend my computer suspends properly (all fans and everything stop) but it resumes in about 1-2 seconds.  Like everything turns off and than turns on in a second.  Anybody got any ideas?  My SWAP area is set correctly, I have 4GB RAM and 6.9GB SWAP.

I am running Ubuntu 9.10 x64 with latest updates
NVIDIA GeForce 9600 GT video card.

---

### Post by beetleman64 on 2009-12-10
What type of Laptop are you using? I find that I have issues with suspend with my Fujitsu-Siemens Amilo Li 2727 where it suspends and then shuts down when you try to start it again. I'm not saying that I can be of much help, but different Laptops may or may not have issue.

---

### Post by vmanisme on 2009-12-10
> **beetleman64 said:**
> What type of Laptop are you using? I find that I have issues with suspend with my Fujitsu-Siemens Amilo Li 2727 where it suspends and then shuts down when you try to start it again. I'm not saying that I can be of much help, but different Laptops may or may not have issue.

Desktop, not laptop.

---

### Post by Xbehave on 2009-12-10
what does free give you before you suspend, it may be that you don't have enough free swap to suspend (you need enough swap to fit all your ram, so  if your already using a lot of swap, you can't suspend)

---

### Post by viktorzk on 2009-12-10
Try installing the uswsusp package and running sudo s2ram in terminal. I have no idea what it does, but it worked for me.

---

