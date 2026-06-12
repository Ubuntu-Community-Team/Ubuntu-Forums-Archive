---
title: "Ubuntu changes drive order with multiple HDDs"
date: 2012-02-05
forum: General Help
---

### Post by apr64 on 2012-02-05
My motherboard is GIGABYTE GA-890GPA-UD3H, and I have 4 internal HDDs. The first one (sda) contains various Ubuntu versions. Others HDDs contain Windows XP, Windows 7, and data. However the drive order changes when there is a kernel/software update (all the 4 HDDs are connected). After a reboot, sda has become sdc. All the HDDs are repositioned. Can someone please explain how and why this happens. Is there a way to stop this from changing?

---

### Post by aasdfasdfg on 2012-02-05
This is a good question. One may naively expect drive ordering to remain intact after reboots, but this is not necessarily the case. Personally, the only times I have had issues with drive ordering changing was after repartitioning disks. However I have heard of situations like yours as well.

Essentially, there is no guarantee that /dev/sd* entries will be preserved after a power cycle. This is why UUIDs (universally unique identifier) were introduced. This guarantees a unique way to label a drive between power cycles.

For more information, see [wikipedia]("http://en.wikipedia.org/wiki/Universally_unique_identifier") or a [practical use]("https://help.ubuntu.com/community/Grub2#line-76")

---

### Post by mcduck on 2012-02-05
It pretty much depend on your motherboard. Linux assigns drive names based on the order in which the drives are detected on boot, and as some motherboards can detect drives in different order on every boot (or based on if there are removable drives connected or not, for example) the device names in Linux might change.

Like aasdfasdfg said, the solution is simple and easy. Configure your drives using UUID or partition label instead of the device name.

---

### Post by apr64 on 2012-02-05
Thanks a lot guys! :D

---

