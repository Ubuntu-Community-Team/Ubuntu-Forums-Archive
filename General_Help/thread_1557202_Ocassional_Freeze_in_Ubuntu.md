---
title: "Ocassional Freeze in Ubuntu"
date: 2010-08-20
forum: General Help
---

### Post by gloken on 2010-08-20
I've been having fairly random freezes in Ubuntu. The desktop freezes, and keyboard/mouse are unresponsive. 

As far as I can tell it's a random problem, with no obvious error, that I can't reliably reproduce, and we all know how much fun those are to trouble shoot. 

Any thoughts on how I can get to the bottom of this? I've got a fresh install of Lucid, with a few updates to drivers and kernel, but otherwise it's pretty close to "out of the box."

The Disk and Video card are brand new, so I'm not inclined to blame them.

---

### Post by NTHQ on 2010-08-20
Unfortunately this is happening to many people and it has still not been solved.
 
[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

---

### Post by s0rc3r3r on 2010-08-20
Same here.
Its happening like a Freeze a day.I was just using Empathy and Mozilla..Not too many websites were opened in Mozilla too..just 2 tabs.
Stilll ubuntu Froze and had to hardboot it.
:(

Hope there is a way to check it and  find it out..Can anyone tell me which log should I check for issues like these?

---

### Post by gloken on 2010-08-20
> **s0rc3r3r said:**
> Same here.
Its happening like a Freeze a day.I was just using Empathy and Mozilla..Not too many websites were opened in Mozilla too..just 2 tabs.
Stilll ubuntu Froze and had to hardboot it.
:(

Hope there is a way to check it and  find it out..Can anyone tell me which log should I check for issues like these?

Judging from the link, I think we get to wait and pray.
Honestly I'm kind of shocked, I've had some issues over the year with Ubuntu, but this looks like a very common, and very critical bug.

---

### Post by dino99 on 2010-08-20
hi guys,

when you have issues, take mind to look at usefull errors logged into .xsession-errors (/home, ctrl+h to unhide) and into system/admin/logviewer

check that your driver is activated: system admin hardware driver

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

some freezes are due too some memory lack when the user install and run many apps at the same time and want special effects (compiz, emerald)
so you might ask what your system is able in some cases

---

### Post by Rubi1200 on 2010-08-20
This link to a launchpad bug report might help shed some light on what others have experienced and/or tried in terms of finding solutions:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

---

