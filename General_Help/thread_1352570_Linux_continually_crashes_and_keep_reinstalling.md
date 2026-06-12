---
title: "Linux continually crashes and keep reinstalling"
date: 2009-12-11
forum: General Help
---

### Post by scuba117 on 2009-12-11
I have re-installed Ubuntu a total of 12 times in the last 30 hours. Every time i get it set up how i like it, when i restart 80% of the time it comes up with some error on the black prompt and i have to start from scratch..

how can i prevent this repeated failure of crap? it seems extremely unstable :P

(most recent error is not syncing vfs unable to mount foot fs)

---

### Post by earthpigg on 2009-12-11
hi,

try accepting all the updates (see code below), restarting so low-level kernel changes and whatnot have a chance to kick in and take effect, and ***then*** get it set up how you like.

```
sudo apt-get update && sudo apt-get upgrade
```

let us know if that does it for ya.

---

### Post by scuba117 on 2009-12-11
i did that before, install everything and restart. then the next time i restart it screwed up :/

ty tho

---

### Post by audiomick on 2009-12-11
have you excluded the possibility of a hardware problem?

---

### Post by PRC09 on 2009-12-11
Does it run fine without whatever it is you are installing and setting up? Maybe its not liking something you are installing or configuring.....

---

### Post by scuba117 on 2009-12-11
im not sure how to exclude hardware as a possible cause other than removing a piece of hardware, restarting (and repeating) :P

a lot of the time it's Compiz (the one you get from the download center) when i set it up to do the advanced desktop effects and what not. that and some minor aesthetic adjustments

---

### Post by PRC09 on 2009-12-11
Maybe post your machine make and model and hardware specs.Kind of hard to tell whats what without knowing that.There are a number of posts with compiz having problems with certain hardware configurations .I am not an expert on this but will do what I can....

---

### Post by earthpigg on 2009-12-11
> **scuba117 said:**
> im not sure how to exclude hardware as a possible cause other than removing a piece of hardware, restarting (and repeating) :P

a lot of the time it's Compiz (the one you get from the download center) when i set it up to do the advanced desktop effects and what not. that and some minor aesthetic adjustments

you could start with the hard drive :D

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

