---
title: "Dual Booting w/ Shared User Profile"
date: 2010-02-17
forum: General Help
---

### Post by CeilingKitten on 2010-02-17
Hey everyone,

I am dualbooting ubuntu and windows xp.  I was wondering though is it possible to store my user profile on a separate partition.

Ideally i would like a spare NTFS partition that contained both my windows and linux user account so i would have the same desktop / my documents etc,. no matter which os i boot into instead of having double of everything, or storing them in some other less convenient place.  Is it do-able? i know i cant install ubuntu to ntfs but it can auto-mount the partition on boot.  Would that work when i try to login to my userprofile.  

Any advice or suggestions are welcome.

Thanks
~CK

---

### Post by Girya on 2010-02-17
> **CeilingKitten said:**
> Hey everyone,

I am dualbooting ubuntu and windows xp.  I was wondering though is it possible to store my user profile on a separate partition.

Ideally i would like a spare NTFS partition that contained both my windows and linux user account so i would have the same desktop / my documents etc,. no matter which os i boot into instead of having double of everything, or storing them in some other less convenient place.  Is it do-able? i know i cant install ubuntu to ntfs but it should be able to auto-mount the partition with my userprofile at boot before i login.  

Any advice or suggestions are welcome.

Thanks
~CK

you can auto mount a ntfs partition at boot to store data, music, etc so you can access it from either xp or ubuntu. 

do you have a 2 ntfs partitions?

if you dont you should create a second one so you can write to a data partition without having to worry about accidentally screwing up system files on the partition that contains the xp os. 

check out these man pages: fstab(5), blkid, mount

---

### Post by CeilingKitten on 2010-02-17
Thanks Gyra, I don't think i worded it right. =] So i'll give it another try.

I Guess what I was trying to ask is can i relocate my whole user profile in ubuntu to the spare NTFS partition as oppose to just saving the files there?

I am able to set it up to auto-mount fine, i'm just trying to find out if i can move my profile without worry of next time i login it says user account is missing or something else bad happening.

I basically want to do this
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)
but save both the windows and the ubuntu user accounts on the same NTFS partition.  

Partitions
[WINDOWS][UBUNTU][USER ACCOUNTS]

This way should i ever have to reinstall either OS, all my user configurations and personal data would remain intact.

---

### Post by dcstar on 2010-02-17
> **CeilingKitten said:**
> Thanks Gyra, I don't think i worded it right. =] So i'll give it another try.

I Guess what I was trying to ask is can i relocate my whole user profile in ubuntu to the spare NTFS partition as oppose to just saving the files there?

I am able to set it up to auto-mount fine, i'm just trying to find out if i can move my profile without worry of next time i login it says user account is missing or something else bad happening.

I basically want to do this
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)
but save both the windows and the ubuntu user accounts on the same NTFS partition.  

Partitions
[WINDOWS][UBUNTU][USER ACCOUNTS]

This way should i ever have to reinstall either OS, all my user configurations and personal data would remain intact.

You cannot put Linux System folders on non-Linux filesystems, they do not support all the necessary features that Linux requires.

NTFS in **not** a Linux filesystem.

---

### Post by jamesisin on 2010-02-17
Your /home directory (as pointed out) contains things vital to your OS (beyond your personal files).  I would look into creating a common personal storage area accessible by both machines.  If you have a storage hdd already, just add a folder called MyShite and distribute links on both operating systems to items within that folder (a documents link in both My Documents and Documents; a Tunage link in both My Music and Music; &c.).

---

### Post by CeilingKitten on 2010-02-17
Alright, Thanks for all the help everyone.

---

