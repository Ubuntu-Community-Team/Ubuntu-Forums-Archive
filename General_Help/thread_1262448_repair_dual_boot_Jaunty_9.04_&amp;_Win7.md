---
title: "repair dual boot Jaunty 9.04 &amp; Win7"
date: 2009-09-09
forum: General Help
---

### Post by charonred on 2009-09-09
_Short story_;
Friends PC has Jaunty & now Win7 installed on same disk, but only Win7 is bootable; so how do I fix the boot so he can choose which OS to run.
[U]
Long story[/U];
Friends PC got messed up by another person installing Windows XP home on the same disk as Jaunty 9.04 was installed.

PC has 2 x 1TB drives and 1 x 500GB drive (2/3 full); and a 200GB disk with XP on it, but that had a head crash last week and is now a paperweight.

The 10 month old 1TB drive was also having problems and is going back under warranty as soon as this mess is sorted. Last week I installed Jaunty to a brand new 1TB drive and copied all data from the failing one across to it.

Friend is absolutely new to Ubuntu and needs the familiarity of XP for his normal PC work while he slowly learns Ubuntu.

After the 200GB died, rather than bother me to clear the 500GB and install a fresh XP on it, he got this other 'expert' (friend of a friend of a friend) to install it; trouble is he installed to the new 1TB disk and made Jaunty unbootable.

The resulting XP Home install was only 5GB with 500MB free space - needless to say XP wouldn't run properly, so I used a live Jaunty CD & Gparted to resize the XP partition to 60GB, but XP would just hang, so I then installed Win7 RC1 to the resized partition instead.

All the data and Jaunty install on the remaining 900GB partition is still there, but there is no boot option for it, it just boots to Win 7. 

Don't want to re-partition or format the disk as friend doesn't want to risk loosing 3+ years worth of downloads etc that have been copied from 'failing' 1TB disk - just need to fix the boot so he can choose Jaunty or Win 7.

---

### Post by lindsay7 on 2009-09-09
You can try this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by charonred on 2009-09-09
thanks lindsay7,
sounds easy enough, I'll give that a shot when I go over his place later this week -  I'll do the smart thing and disconnect the other drives first.

---

### Post by lindsay7 on 2009-09-09
You should not need to to that.  Just try this, it should not hurt anything.

---

### Post by Muscovy on 2009-09-09
I had some simmilar issues when putting in a W7 partiton beside Ubuntu. Installing grub and updating the W7's location in grub worked for me.

---

### Post by charonred on 2009-09-09
I've messed up a few drives myself over the years, and now find it easier and safer to disconnect other drives when installing OS's;  and with only 1 drive connected, there's no confusion over which one is which during install. 

Normally I prefer not to dual boot systems; I'd rather install different OS's to separate disks, and use F12 to choose which to boot - and if there's not enough disks available, then there's always Virtualbox.

---

