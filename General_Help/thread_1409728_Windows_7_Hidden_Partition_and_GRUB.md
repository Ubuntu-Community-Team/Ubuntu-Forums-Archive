---
title: "Windows 7 Hidden Partition and GRUB"
date: 2010-02-17
forum: General Help
---

### Post by Calcipher on 2010-02-17
I was installing Ubuntu on my new laptop (with plans to dual boot with Win 7) and, I'll admit, I did something stupid.  You see, there was a 1 meg free space before the Windows 7 'hidden partition' and it was driving me nuts.  So, what I did, was use gparted to move the hidden partition to the start of the drive (yes, a 1 meg move).  Install of Ubuntu went off without a hitch, but after reboot things went a bit differently.  The Recovery partition shows up as a possible boot partition in GRUB, in Windows 7 I can now see the recovery partition as a normal NTFS drive, and I can no longer use the features that the partition gives.  I know this might be more of a 'ask on a Windows forum' question, but I was hoping someone else had done something like this and knew how to restore the hidden partition to being, well, hidden.

---

### Post by Dies on 2010-02-18
Open gparted, right-click the partition and select "Manage flags", make sure hidden is still selected.

---

### Post by Calcipher on 2010-02-18
Thanks!

---

