---
title: "Help: Root File System Error..."
date: 2006-05-20
forum: General Help
---

### Post by master5o1 on 2006-05-20
I am being forced to use my Slax LiveCD because I have this Root FIle System error with Ubuntu...

I tried starting it up and this is what happened when it started checking Root File System:

```
* Checking Root File System...
/ Contains a file system with errors, Check enforced.
/:
Unattached inode 1310793.
/:UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
[CENTER](I.E., without -a or -p options)[/CENTER]

[INDENT]* fsck failed. Please repair manually and reboot. Please not
* that the root file system is currently mounted read-only. to
* remount it read-write:
*[CENTER]# mount -n -o remount,rw /[/CENTER]
* CONTROL-D will exit from this shell and reboot the system.[/INDENT]

bash: lesspipe: command not found
bash: dircolors: command not found
root@(none):~#
```

Any ideas? Help needed (I cannot afford to reformat as I have images and stuff...but if that's the only way, i can use a 4GB HDD as a backup for them:-?)

Btw: 
20GB HDD is Ubuntu
4GB HDD is Linspire
750mhz processor
320MB SD RAM
8MB Nvidia Vanta LT 2X AGP

(Old compaq computer)

Thanks...

---

### Post by user1397 on 2006-05-20
I have had this *_exact_* issue, so don't worry.  just curious, did it happen after turning it on after a while of being turned off?

---

### Post by master5o1 on 2006-05-20
I turned it off at first, then accidentally SHUT IT OFF by the switch (on/off switch at front)...I didnt think of it at all, because I thought I had done it like that a few times and it wouldn't hurt it. But when I turned it on this morning (at about 11:00am NZST) I had that error...so pressed ctrl+D to turn off and use slax...

---

### Post by master5o1 on 2006-05-20
P.S. It's Ubuntu 5.10 :-)

---

### Post by user1397 on 2006-05-20
Yes this happens when you turn the computer off weirdly and/or u turn it on suddenly after long hours of being turned off.  my solution:
type 
```
fsck
``` and press enter
then just say yes to everything and eventually it will stop
then just type 
```
sudo reboot
``` to reboot and you should be fine.
my long-term solution: leave my computer on forever!!!!!!!!!!!!!!!!:D
when you're done please post back if it worked!

---

### Post by master5o1 on 2006-05-20
yeah, thanks...I will do that now:-D

---

### Post by master5o1 on 2006-05-20
YAY! Thanks...It worked perfectly and I am now using my Ubuntu!!!!

---

### Post by user1397 on 2006-05-20
[quote=master5o1]YAY! Thanks...It worked perfectly and I am now using my Ubuntu!!!![/quote] Awesome! the reason that happens (or so i've heard) is that some of the logical blocks on the hard drive get read wrong after the pc is turned on suddenly or if you turn it off by using the button, not the correct way.
oh well, there's a solution to it, so im sticking to it! :D

---

### Post by master5o1 on 2006-05-20
yeah, and a liveCD, forum, and help is good too! :-D

---

