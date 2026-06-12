---
title: "Doesn't start ubuntu software center on ubuntu 10.04 LTS"
date: 2011-06-24
forum: General Help
---

### Post by andreah on 2011-06-24
Hi everybody this is my first thread so please forgive my mistake

I can't open ubuntu software center and some other applications like rhythmbox music player
when i tried to launch ubuntu software center from terminal says

"andreah@andreah-laptop:~$ software-center
Inconsistency detected by ld.so: dl-lookup.c: 859: _dl_setup_hash: Assertion `(bitmask_nwords & (bitmask_nwords - 1)) == 0' failed!"


please help me i have n idea what to do and i don't want to reinstall (again)
 bye ty

---

### Post by dino99 on 2011-06-24
hi and welcome,

seems that software-center installation is borked. But you can use better tool: synaptic (myself never use software-center)

goto menu: system/admin/synaptic

then remove/purge software-center (to clean the borked installation) then reinstall it

---

### Post by andreah on 2011-06-24
I do what you say doesn't work.
i have no idea what i have to write to help me get help from others

When i run " sudo apt-get repair" say: segmentation fault

---

### Post by dino99 on 2011-06-24
> **andreah said:**
> I do what you say doesn't work.
i have no idea what i have to write to help me get help from others

When i run " sudo apt-get repair" say: segmentation fault


NEVER said to do that :( please take time to read and follow my previous post) meaning:

into a terminal:
sudo synaptic

or as said previously, use the menu on top taskbar, and select: system -> admin -> synaptic

---

### Post by andreah on 2011-06-24
yap. i do wat you say and after the new installation the software center doesn't open
i added the other line cause is a problem too and i think may help to solve my problem

whatever

 i repeat: reinstall software center from synaptic doesn't work.
thanks anyway

---

### Post by andreah on 2011-06-24
Hi,
I try to explain my problem in a better way. someday ago my pc hpcompaq nx6110 doesn't start, the boot finish whit a written "INTIFRAMS". i insert the installation cd, repair something i don't know what and my sistem start , but i have some problem:

-ubuntu doesn't open some application like ubuntu softwarecenter rhytmboxmusicplayer computerjanitor, maybe more i don't check all applications.

-if i run from terminal sudo get-apt update or sudo get-apt upgrade or other sudo get-atp it says 
"segmentation fault"

-if i try to run ubuntu softwarecenter from terminal it says "andreah@andreah-laptop:~$ software-center
Inconsistency detected by ld.so: dl-lookup.c: 859: _dl_setup_hash:  Assertion `(bitmask_nwords & (bitmask_nwords - 1)) == 0' failed!"

PLEASE HELP I HAVE NO IDEA WHAT TO DO

---

