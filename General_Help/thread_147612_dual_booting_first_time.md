---
title: "dual booting first time"
date: 2006-03-20
forum: General Help
---

### Post by trance565 on 2006-03-20
ok, here's the deal, i have a 160 gig hdd, with kubuntu installed on it, i've been using it for a while now ... (6 weeks?)
well the other day i ordered a 250 gig hdd, i plan to use 90-100 gigs for windows, and the rest for kubuntu

so I installed windows, with the 160 gig unplugged, so i wouldnt have to format it etc. after installing windows, and installing all the drivers and whatnot for my system, i shut down, plug in the 160, and turn it on, it boots straight to windows.... isnt it supposed to ask which OS i want to boot into?

---

### Post by FLeiXiuS on 2006-03-20
The Windows install completely kills the block GRUB has installed to the MRB.  Keep in mind, the MBR isn't located on the hard drives.  There's really no way to prevent it.  But you can fix it!

Check this out for the time being...

[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

---

### Post by trance565 on 2006-03-20
edited temporarily

---

### Post by trance565 on 2006-03-20
ok, fixed it so i can get into linux, but still, cant choose which OS to go into, cant get into windows now...

i put windows xp in the boot menu and it still doesnt work


i put
"title		Windows XP Professional
root		(hd1,0)
makeactive
chainloader +1"

as im using 2 hdd's and it's the first partition on the 2nd drive, im assuming thats the location, it gives me an error of

it's set up like this
hda1 - my linux instalation
hda5 - swap
hdb1 - windows
hdb2 - storage for linux

filesystem type unknown.... partition type 0x7

---

### Post by trance565 on 2006-03-20
bump, really need help here, would love to get back into windows so i can get premier up and running again along with a few games

---

### Post by incubus on 2006-03-21
Fleixius, are you sure? I think the MBR is located in the hard drive. 
[http://en.wikipedia.org/wiki/MBR]("http://en.wikipedia.org/wiki/MBR")

In fact, that could be the problem.

trance, in which hard drive did you install GRUB? Is that the one that is listed in the boot order in your BIOS setup? You didn't switch cables, right?

Plus, when you setup GRUB you install the boot files in some directory (usually /boot/grub/). Can you double check you did this step and this directory is there with all files?

incubus

---

### Post by trance565 on 2006-03-21
grub is on hda1 which is the same partition of hdA linux is on, as hdA2 is the mem. swap

windows is on hdB1

hdA is still set as primary, hdb is set as slave as i just got it a couple days ago

boot order in bios is
hdA 
hdB
(they have long names, so i dont feel like memorizing or writing them down as they dont matter)

---

### Post by trance565 on 2006-03-22
bump

---

### Post by trance565 on 2006-03-22
ok, would it be easier to reinstall windows, and then edit the windows boot kernel to give me a choice between linux and windows?

---

### Post by trotski on 2006-03-22
Are you able to see the Grub menu on boot-up at all?  Do you need to hit the escape key to view it?  You should see an assortment of Ubuntu options at the very least.

---

### Post by trance565 on 2006-03-22
yea, i get to the menu no prob, but when i choose windows, it gives me unknown file system type, partition blah blah blah error

last night i didd apt-get update, to update evthing and see if that would have helped, and it didnt, in fact, now when i log in it sets screen res to 640x480, and when i re adjust all the fonts are too small to see, but i'll start another thread for that issue

---

### Post by trotski on 2006-03-22
OH! I think I remember this problem.  WinXP hates being the number 2 drive.  It likes to think it is on the master drive, I believe.  It has ... issues with its masculinity or something (can't be on an extended partition, either...)

Anyway, try this.  Put this in the Windows entry in menu.list:

map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

---

### Post by trance565 on 2006-03-22
so, instead of changing evthing in the boot menu and switching hard drives from slave to master master to slave, just put taht under the windows thing ... got it, i'll give it a try in a few minutes

... wiait

put that after the root (hd1,0) or before?

nvm got it, w00t game time!

---

