---
title: "Dual boot Raid 0 :["
date: 2010-05-16
forum: General Help
---

### Post by v1ad on 2010-05-16
hey guys i am trying "again" to dual boot on my gaming computer, and i am failing miserably. i boot the cd, it detects the hard drive i set the partitions and press finish and either on the partitioning or the files copying the installer crashes. what can i do to make it work with raid 0 (nvidia chipset).

---

### Post by v1ad on 2010-05-17
Bump ?

---

### Post by john newbuntu on 2010-05-17
If you have not already done so, please read the documentation for installing Ubuntu on fakeraid systems (esp. the section for Karmic 9.10 presuming you are installing either Karmic or Lucid):
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You need to use manual partitioning during installation.  It basically comes down to using /dev/mapper/<whatever> as your disk device rather than the individual disks(/dev/sda /dev/sdb etc.) for creating partitions, filesystem and installing grub.

Also take a look at this: [http://ubuntuforums.org/showthread.php?t=1452822](http://ubuntuforums.org/showthread.php?t=1452822)

---

### Post by v1ad on 2010-05-26
k i got a problem here with grub. i coppied and partitioned everything and tried to install grub. failed miserably. tutorials are a bit outdated and it did not turn out like planned, now can't boot into windows or linux. help :[

---

### Post by v1ad on 2010-05-26
k  got it to boot linux but i have no splash screen so i would be able to select windows.

---

### Post by v1ad on 2010-05-26
k figured it out went through hell came back, made it work.

---

