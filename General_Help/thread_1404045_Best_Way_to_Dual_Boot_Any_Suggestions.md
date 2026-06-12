---
title: "Best Way to Dual Boot? Any Suggestions?"
date: 2010-02-11
forum: General Help
---

### Post by Palartzski on 2010-02-11
ive been using windows for way too long now and im willing to get used to using ubuntu, but i dont want to use it as my only OS. therefore, ive been trying to get both OS's to work as a dual boot on my laptop. however, since im limited to only one hdd, i have to rely on GRUB to run correctly in order to get everything to run smoothly. to keep a long story short, i have had the worst luck with using GRUB to dual boot between the two, and im looking into do it differently. does anyone have any suggestions? ive been told that i can always virtualize ubuntu or do a wubi install. are there any advantages from one to the other? any help would be great!

---

### Post by subodh.rohilla on 2010-02-11
If you want to get best ubuntu experience then shrink your windows partition and do full install of ubuntu in new parttion ( around 10 gb is best) . 

With wubi install , the data is stored in virtual disk so the performance is realtively poor. When , it comes to virtualization , if you have enough ram and good Graphics card , you can run ubuntu in virtual box.

---

### Post by t4thfavor on 2010-02-11
Best way to dual boot is with a removable drive sled, aside from that GRUB is the most effective way to get the best speed out of your linux install. I have been using it for years, without so much as a few (self induced) hiccups.

Basically if you install Ubuntu first, Windows will wipe it out, or at least the bootloader, and you will have to manually install it again./

---

### Post by Palartzski on 2010-02-11
okay well how would this exactly happen? the reason i am considering other options is because i havent had much luck with GRUB. i first installed windows 7. before that, i created a partition for it on my hdd, and then left the rest unallocated. i installed windows 7 to the partition i created. then, i installed ubuntu and everything seemed to have worked fine for 2 days. today, each time i slected windows 7 from the GRUB prompt, it would not load. all i would see was a blinking cursor and the hdd would stop spinning. if i loaded ubuntu once i rebooted my pc, it would run fine and the hdd would be running just fine.

---

### Post by john newbuntu on 2010-02-11
Use this first to restore window7.  Make sure your startup problems are fixed completely.
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

As far as GRUB2 goes(which I am assuming you have - check this using grub-install -v.  It should be like 1.97 or so), you need to install it to your MBR.  Boot from an Ubuntu liveCD.  Then type these from a terminal:
   sudo fdisk -l
   sudo mount /dev/sda5 /mnt       [presuming /dev/sda5 is linux root partition]
   sudo chroot /mnt
   sudo grub-install --root-directory=/mnt /dev/sda --recheck
   sudo update-grub
   sudo umount /mnt

   Now reboot and finally after logging in to linux:
   sudo update-grub2

---

### Post by Palartzski on 2010-02-11
alright i will give this a shot. lets say if i just completely wipe out the hdd and start off with a clean slate. if i reinstall everything again, should i still go through with installing GRUB to my MBR as you mentioned?

---

### Post by philinux on 2010-02-11
> **Palartzski said:**
> alright i will give this a shot. lets say if i just completely wipe out the hdd and start off with a clean slate. if i reinstall everything again, should i still go through with installing GRUB to my MBR as you mentioned?

Instead of using grub you can use easybcd for vista and win 7.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

For grub2 you'll need the beta version.
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

Works a treat on GF's lappy.

---

### Post by khelben1979 on 2010-02-11
The best way to dual boot Ubuntu (or any other Linux distro.) would be to have Windows and Ubuntu kept separate on different harddrives. More safe and prevents future hassles if GRUB would mess up something.

---

