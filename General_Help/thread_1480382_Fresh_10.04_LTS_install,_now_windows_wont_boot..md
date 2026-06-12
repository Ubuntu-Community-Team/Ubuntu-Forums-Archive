---
title: "Fresh 10.04 LTS install, now windows wont boot."
date: 2010-05-11
forum: General Help
---

### Post by utn on 2010-05-11
Hello,
I used to have Ubuntu 9.10 and Windows XP living in harmony on my HD but one day I felt I needed to re-size a partition and then grub ceased to work and nothing would boot. Because of this, yesterday I installed Ubuntu 10.04 on the 9.10 partition and now grub recognizes Ubuntu and Windows again and Ubuntu boots just fine. But when I try to boot Windows the bios speaker just beeps on forever and I only get to look at a black screen with a flashing underscore in the top left. I have tried going to the terminal and typing update-grub with no improvement. And it seems the partitions are setup properly so I don't know why Windows won't boot. Windows is on HD(0,1)NTFS, Ubuntu is HD(0,2)ext3, and swap hd(0,3). Any ideas?

Thank you.

---

### Post by dcstar on 2010-05-11
> **utn said:**
> Hello,
I used to have Ubuntu 9.10 and Windows XP living in harmony on my HD but one day I felt I needed to re-size a partition and then grub ceased to work and nothing would boot. Because of this, yesterday I installed Ubuntu 10.04 on the 9.10 partition and now grub recognizes Ubuntu and Windows again and Ubuntu boots just fine. But when I try to boot Windows the bios speaker just beeps on forever and I only get to look at a black screen with a flashing underscore in the top left. I have tried going to the terminal and typing update-grub with no improvement. And it seems the partitions are setup properly so I don't know why Windows won't boot. Windows is on HD(0,1)NTFS, Ubuntu is HD(0,2)ext3, and swap hd(0,3). Any ideas?

Thank you.

Did you upgrade or do a fresh install?

If you upgraded you may still be using the legacy grub which may have to be replaced by the newer version.

There is also an issue of hard drive boundary alignment which may be relevant:

[http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems](http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems)

---

