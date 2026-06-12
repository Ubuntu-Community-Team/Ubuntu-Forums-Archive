---
title: "Suddenly unable to load Ubuntu"
date: 2012-07-05
forum: General Help
---

### Post by ImKukie on 2012-07-05
I have used ubuntu for about 2 years upgrading when asked starting with  vsn 9 thru 11.10 or whatever that last version was before 12 came out.  For the past 2 months every once in a great while my laptop would shut  down unexpectedly and upon reboot I would get to the screen that would  ask me if I wanted to load an earlier version or a generic version. I'd  choose generic (recovery mode) and all would be right with my world  again. A few days ago however, after a normal shut down the night  before, when I logged on to my laptop I got that screen again but this  time (for the 1st time ever) after the booting ubuntu splash screen, it  brought me to a screen with a bunch of stuff I didn't understand &  eventually ended me with a line that said... 

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramf s)

~ I have no clue what that means or how to fix it~

Additional (potentially useful) info
In my bios set up utility I ran a hard drive self test & it said #2- 07 Fail
No clue what that means but I fear it's not good. 

I  also tried F12 at boot up which lets me load from LAN (whatever that  is) and it brought me to the same screen where I could choose recovery  mode, safe mode, memory test or previous versions - I choose PREVIOUS  VERSIONS just to be different & got the following text...

Mount: Mounting /dev/disk/by-uuid/f5c692b2-6fe1-4430-aeaf-8fe45d20b736 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

 BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)



I read in a forum regarding the 8.10 version  of ubuntu where they were describing a similar issue & they said to  turn the "sata mode" in bios from "ahci" to "raid" - I have no clue  where to find that or how to do it or if it will even work. When I go  through my screens in the set up utility none refer to anything related  to that.

I have an HP (Compaq) Nx9600
Processor Intel (R) Pentium (R) 4 speed 3600MHz
System Memory 2048
BIOS Version F.32
KBC Version 36.31

There has never been windows of any kind since I got it 
It  was preloved & wiped when I got it & the battery never worked  so I have been tethered to a wall for a while but for $120 for a 17 in  screen... I was happy.

---

