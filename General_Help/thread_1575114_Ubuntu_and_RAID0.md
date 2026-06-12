---
title: "Ubuntu and RAID0"
date: 2010-09-15
forum: General Help
---

### Post by but2002 on 2010-09-15
I have Windows 7 installed to a RAID 0 Partition, and I installed Ubuntu to an older IDE 80 GB drive of mine

While I installed, I had unplugged the RAID 0 drives to prevent the installer from seeing them and attempting to make any modifications (Saftey first, right?)

Ubuntu's done installing, and I can boot into Windows 7 fine.  I shut down.

I boot into Ubuntu, and I can't mount the RAID 0 partition.

gparted shows them as seperate drives (Normal?)

The BIOS treats it as NVIDIA STRIPED.

How can I mount this RAID0 partition in Ubuntu?

---

### Post by yota on 2010-09-15
Your RAID is not a "true" RAID, it's a software RAID implemented in the nvidia driver usually known as a "fake RAID".

Look [here]("http://ubuntuforums.org/showthread.php?t=629459") for a quick (but maybe a bit outdated) procedure on how assemble the drives and mount the partition in ubuntu.
[Here]("https://help.ubuntu.com/community/FakeRaidHowto") you can find more information about fake raids in ubuntu, just note that a lot of informations are in the direction of installing the OS on the RAID, which does not aplly here...

Long story short... get dmraid! :-)

---

### Post by but2002 on 2010-09-15
Brilliant!

That was easier than I expected!

---

### Post by ronparent on 2010-09-15
As you noted, gparted will not find raid partitions in 10.04. You have to install a small program, kpartx, which will enable gparted to see raids. To get windows into your grub just boot into 10.04 and run 'sudo update-grub' from a terminal. The grub menu should then find windows.

---

### Post by sinner99 on 2010-10-28
awesome! thanks for the kpartx n cheers to poster ^^ for that. just a heads up, i've had about 10x1.5tb seagate drives and they have ALL had at least 4 bad sectors new out of the box. I've lived and breathed seagate forever, soon to change I believe. hope the ssd's come down alot more!

---

### Post by dcstar on 2010-10-29
> **yota said:**
> **Your RAID is not a "true" RAID**, it's a software RAID implemented in the nvidia driver usually known as a "fake RAID".
.........

That is more true than most people would realise.

*RAID 0* is the exact opposite of RAID - there is no redundancy and you actually double the chances of losing **all** of your data if **one** of the drives fail.

The "R" in RAID means Redundant, the term "RAID 0" is a total lie as using it reduces the statistical life of the combined drives by 50% - in truth it is Anti-RAID.

---

