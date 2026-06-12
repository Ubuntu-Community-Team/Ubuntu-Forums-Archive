---
title: "having trouble with dual boot"
date: 2009-09-29
forum: General Help
---

### Post by r16l26r36 on 2009-09-29
i am in the process of setting up two computers with dual boot of windows xp professional and ubuntu 9.04 and unfortunately ran into a few hickups
1. after i installed ubuntu i loaded into windows, then back to ubuntu and found that my neatly partitioned drive had decided to leave ubuntu only 2.5 gigs of space.[I] why did this happen and how do i prevent this from happening again?

[/I]2. to fix this i deleted ubuntus partition, cut windows back down to half of the drive and reinstalled ubuntu on the rest, leaving 1000 megabytes for a swap area, after restarting my computer, i was presented with the grub loader, now without windows xp professional.
i have checked and it is still installed. [I]why did this happen and how do i fix it?

[/I]i used the instructions here [http://ubuntuforums.org/showthread.php?t=474883](http://ubuntuforums.org/showthread.php?t=474883) to restore windows to the list, but the instructions seems case sensitive and now when i try to boot windows from the grub list, it simply tells me its an invalid device/command i dont recall which.

this is on a partitioned 80gb drive if that helps in the least

---

### Post by utnubuuser on 2009-09-29
try> [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)
or> [http://geniushackers.com/blog/2008/04/02/recover-windows-mbr-using-ubuntu-live-cd/](http://geniushackers.com/blog/2008/04/02/recover-windows-mbr-using-ubuntu-live-cd/)

---

### Post by r16l26r36 on 2009-09-29
well, simple enough to execute except for two complicating factors.
1. in live session i cant seem to connect to the internet
2. in normal ubuntu i cant get the program i just get this
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
yes, i checked off universe. i imagine this has to be done in live session?
do you know of anyway that doesnt require the use of the internet? i still have both my ubuntu and windows install disks.

but for now its really time to call it a night. hopefully a solution will present itself tomorrow.

---

