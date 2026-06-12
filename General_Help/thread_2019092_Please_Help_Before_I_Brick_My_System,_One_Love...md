---
title: "Please Help Before I Brick My System, One Love.."
date: 2012-07-07
forum: General Help
---

### Post by SavageIntoxicant on 2012-07-07
Hello Ubuntu Forum Community,  

I just want to say I love the linux sentiment,  Ive been restoring my computer and learning to use ubuntu for a few years,  but Im at a point where I have an odd problem,  not sure how to go about this, 

Ive been cobbling together a desktop environment with tons of different builds,  my 2 hard drives are a clusterf* of partitions and broken builds,  there seem to be a few bad sectors on each hard drive to make it worse. 

I cant afford a new computer, and I cant seem to ever get a perfect copy of ubuntu no matter how slow I burn it,  so it could be my computer..

Basically I want to install Ubuntu from Ubuntu, over an entire hard drive,  But the hard drive im not using to boot from has bad sectors and a lot of files id like to keep.

I tried Unetbootin it, but when I go to that entry it never works,  and I can never seem to figure out that syntax for grub-boot.cfg or whatever the file is... I havent tried sinking my teeth into this problem for awhile so i thought id ask you guys.


(btw the reason I cant keep my current karmic is because of extremely strange graphical and text errors that would be easier solved with a clean install)

---

### Post by MG&amp;TL on 2012-07-07
Try backing up your files (if you can?) then just install over entire hard drive. As far as I know, the partitioner should make the installer aware of the bad sectors.

Can you explain what you actually want to do more exactly?

---

### Post by GreatDanton on 2012-07-07
1. Which version of Ubuntu are you using? Karmic?

2.Did you try to burn with other burner. If you are using Brasero then I understand you have problems, because most users have problems with Brasero. Try to burn cd with another burner k3b, or xfburn.

---

### Post by oldfred on 2012-07-08
If you want a more advanced way to install from one drive to another you can just boot loopmount the ISO with grub2. You have to make sure ISO is good and it only works with desktop versions.

The only advanced part really is you have to add the boot stanza to 40_custom in grub2 and have to know where the ISO is on the drive.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition

Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[SOLVED] Using grub 2 to boot an iso off hard drive - old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by Habitual on 2012-07-08
Found this [nugget]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html")

---

