---
title: "partition issue"
date: 2011-07-01
forum: General Help
---

### Post by g.a. on 2011-07-01
hi,

i have installed ubuntu 11.04 on a asus eee pc t101tm machine.

i do not remember the steps done during the installation but today i noticed that i had very few space free on my hard disk, so i run gparted and noticed the very strange partition attached.

i'm not expert of partitions and somehow afraid about the warning messages gparted is giving me when i try some solutions.

how can i just have two partitions, one with the original win7 and the other with ubuntu?

please use "basic" terminology in replying me :)

thanks
g.

---

### Post by ajgreeny on 2011-07-01
It looks as if you installed ubuntu from within windows using Wubi.  Was windows running when you installed, or did you boot from a USB flash drive and then create partitions and install as a proper dual boot?

---

### Post by g.a. on 2011-07-01
you are right!

i do not know why but i was not able to create a USB live (i tried in several ways...) and so i runned wubi from windows.

now my laptop sees two booting sequences, one from windows and the other from linux :(

is there a way to recover this unpleasant configuration?

best
g.

---

### Post by westie457 on 2011-07-01
> **g.a. said:**
> you are right!

i do not know why but i was not able to create a USB live (i tried in several ways...) and so i runned wubi from windows.

now my laptop sees two booting sequences, one from windows and the other from linux :(

is there a way to recover this unpleasant configuration?

best
g.

Hi try this it might work.

1 Boot into your Ubuntu installation and use 'Startup Disc Creator' to create your LiveUSB. Ubuntu can read your Windows system so you can find your downloaded .iso file.

2 Check the USB works by booting into it. Changing boot options in the bios if necessary.

3 If all is okay reboot into Windows and uninstall your Ubuntu from Windows Control Panel. You might have to reboot after this -I am not sure because I have not done a Wubi install for 3 years - my memory is failing me at the moment.

4 Insert your USB and boot into it selecting 'Install' when the window appears.

5 At the screen that asks what you want to do, choose the option install alongside other OS. DO NOT ACCEPT THE DEFAULTS as Windows partition will be reduced to the absolute minimum size. Adjust the Ubuntu partition to around 40 GB as a starting size. Click on Install/Forward/Okay, and do the same as prompts appear.

This will give you a working Dual-boot system.

---

### Post by Mark Phelps on 2011-07-01
Do NOT use the Ubuntu installer to shrink your Win7 OS partition to install Ubuntu.  Doing so risks corrupting the Win7 filesystem and rendering it unbootable.

Instead, after removing Ubuntu from Win7, use the Win7 Disk Management utility to shrink the Win7 OS partition.

Also, when in Disk Management, look to see how many partitions are on the disk.  If you already have the maximum of four, do NOT, repeat -- do NOT -- create any new partitions. Doing so will force the conversion of your existing Windows partitions into Dynamic Disks -- which will cause you major grief.  You will have to DELETE a partition to get the number down under four, if you already have the maximum.

---

### Post by g.a. on 2011-07-05
thanks for your replies.

I misunderstood the wubi installation package. I un-installed ubuntu from the windows control panel and now I'm trying to install ubuntu by using an USB boot. 

I have troubles with my laptop (asus eee pc t101mt) since it is not starting from usb but I'm currently investigating the solution...

best,
g.

---

