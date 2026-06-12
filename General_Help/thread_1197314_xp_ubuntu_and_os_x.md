---
title: "xp ubuntu and os x"
date: 2009-06-26
forum: General Help
---

### Post by rudi009 on 2009-06-26
I just installed os X=D> on my already duelboot system .the problem is that grub is not showing os X in the list. just xp and ubuntu...os X starts only with the dvd inserted.help??

---

### Post by Forneus on 2009-06-26
**Configuring GRUB to boot OSx86**

GRUB, the bootloader included with the latest release of Ubuntu, cannot boot your OSx86 partition by itself, so we're going to tell GRUB to pass down the bootstrap to the OSx86 bootloader to let it boot itself. This is a lot easier than it sounds but it requires a little bit of patience and a bit of playing round to get it right.

1) Boot into Ubuntu and open up a terminal.

2) Type *sudo gedit /boot/grub/menu.lst* and enter your password when prompted. This brings up a text editor with instructions on how to play with GRUB.

3) In this file, everything with a hash (#) in front of it is ignored by GRUB; like notes in HTML. Look for where it says *hiddenmenu* or something along those lines, and stick a # in front of it. This is so you don't have to hit Escape every time you want to access your bootmenu and boot OSx86.

4) Next look for the part of GRUB where it displays your installed Kernels. This is normally near the bottom. If you look at it, they follow a basic formula. You'll be using slightly different commands but they achieve the same basic thing.

5) Create an entry for OSx86. Add the following lines:
[I]
title OSx86
root (hd0,0)
makeactive
chainloader +1
[/I]

*title* is the name GRUB will display for the OS. This can be anything you want, mine's been called several things such as 'Hackintosh', 'OSx86' and 'Mac OS X 10.5'. Whatever you're comfortable with really.

*root* tells GRUB what to boot. The command we told it was *(hd0,0)* which is saying to GRUB “Boot from the first harddrive (hd0), using the first partition (,0)”. And this is the bit that'll cause the most trouble. When I was following a tutorial on how to get GRUB to recognise OSx86, I was told to type (hd0,1) which is obviously a completely different partition. If you attempt to boot into OSx86 and you get a message along the lines of *“Error 15: Invalid Device”* just go back into the GRUB menu.lst and change the partition number. Keep changing it until you boot properly

*makeactive* tells GRUB to set the active partition on the root disk to GRUB's root device

*chainloader +1* This command will take the boot sector of the root and use it to boot. Like getting GRUB to load Darwin/Chameleon which will in turn boot OSx86.


[http://geeks.pirillo.com/profiles/blogs/how-successfully-dualboot](http://geeks.pirillo.com/profiles/blogs/how-successfully-dualboot)

---

### Post by rudi009 on 2009-06-26
tried 0,1,2  partitions ...not working...

---

### Post by QIII on 2009-06-26
Can you type

fdisk -l

(that's a lower case L, not a one) in the terminal and post the results?

---

### Post by rudi009 on 2009-06-26
fdisk -l shows nothing!!!!!!!!:(

---

### Post by AlexDudko on 2009-06-26
Type > sudo fdisk -l

---

### Post by rudi009 on 2009-06-26
and now even the windows is not starting up.after selecting windows in grub it says starting and freezes:confused:

---

### Post by rudi009 on 2009-06-26
sudo worked!!!

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a695750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971219+   7  HPFS/NTFS
/dev/sda2            2611       19457   135315873    5  Extended
/dev/sda5            2611       10444    62913721+   7  HPFS/NTFS
/dev/sda6           10444       12794    18878706   83  Linux
/dev/sda7           12794       13055     2098246+  82  Linux swap / Solaris
/dev/sda8   *       13055       19457    51425073   af  Unknown

---

### Post by rudi009 on 2009-06-26
i think that is difficult to read..

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a695750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971219+   7  HPFS/NTFS
/dev/sda2            2611       19457   135315873    5  Extended
/dev/sda5            2611       10444    62913721+   7  HPFS/NTFS
/dev/sda6           10444       12794    18878706   83  Linux
/dev/sda7           12794       13055     2098246+  82  Linux swap / Solaris
/dev/sda8   *       13055       19457    51425073   af  Unknown

---

