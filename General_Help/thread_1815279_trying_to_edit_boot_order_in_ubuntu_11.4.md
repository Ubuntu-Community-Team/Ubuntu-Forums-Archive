---
title: "trying to edit boot order in ubuntu 11.4"
date: 2011-07-31
forum: General Help
---

### Post by dron on 2011-07-31
I have just upgraded from 10.4 to 11.4, I did the upgrade in 2 steps to get to 11.4 The 1st step ( 10.10) all worked well and I had grub working with vista as the default os. When I went to 11.4 grub defaulted to ubuntu and wont let me edit it. I have added a start up manager, gone back to the older version of grub, Edited the config file etc as instructed in several online help pages with no luck. No changes have been made to the start up screen. I am running the amd64 version on a gigabyte board, phernom processor and vista on drive 0 / ubuntu on drive 1

---

### Post by cjack2964 on 2011-07-31
The simplest method to solve this is to run this command to open the grub.cfg file

sudo gedit /boot/grub/grub.cfg

then look for a lin the looks like this

set default="0"

The number refers to which of the OSes listed from left to right to boot by default, so if your prefered OS is the one listed on the far left (or the top depending on your theme in grub2) then you would select 0, if it is 2nd to the left (top) then select 1, 3rd you select 2, and so forth.

I will warn you though, that this change may not survive an update to grub.  Try and remember how you did it in case you ever have to do it again on the fly.

---

### Post by cjack2964 on 2011-07-31
Sorry....i just reread your post more carefully and realized that youve tried this already.....i wouldnt know what to suggest except maybe rebooting twice after the changes to make sure the take effect

---

### Post by dron on 2011-08-05
I still have not managed to change the boot order. Is it possibly related to ubuntu being on the 2nd drive and grub on the 1st drive?  If I replace my boot sector from backup how hard will it be to start the updated ubuntu, the backup was last done before I upgraded from 10.4 to 11.4

---

