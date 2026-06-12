---
title: "Please help! How can I remove grub2?"
date: 2009-12-18
forum: General Help
---

### Post by waww89 on 2009-12-18
I have two hdds. 
hda0: 1.5TB
hda1: 400GB

There was no problem when I had used window xp and ubuntu 9.10 with grub.
Windows xp and Ubuntu had been installed on had1 with different partitions.
When I deleted the windows partition and tried to install windows 7, my computer was out of order.

During booting,, the following messages are showing on screen.

grub loading...
error: no such disk
grub rescue>

 I wanted to reset the whole system. So I deleted the all the partions on hda1(400GB).
Then I did re-partitioning the hda1(400GB) to re-install OS.

However, the same message as the above was displayed on the screen.

How can I fix this problems ?

Is there any way to remove grub boot loader?

I think it is possible to re-install the OS after I delete the grub.

---

### Post by Darael on 2009-12-18
Well, if you've got nothing on the drive you need you can overwrite anything that might be at its start (like GRUB) by booting a live cd and running "sudo dd if=/dev/zero of=/dev/drive-in-question bs=512 count=1", where "drive-in-question" is, well, the device for the drive in question. Be very very careful with this, though, as if you overwrite the wrong device's beginning with zeros by this method you could do serious damage to any data. Well, actually, you'd just overwrite the boot sector and partition table, but it's still a nasty situation to put yourself in, so be careful!

---

### Post by northern lights on 2009-12-18
GRUB most likely resides in the MBR of your first harddisk (watch out: GRUB notation (hd0,0) = device notation /dev/sda1, hd notation having been dropped).

Run```
sudo grub
find /boot/grub/stage1
```to find out for sure.

---

### Post by raymondh on 2009-12-18
> **waww89 said:**
> I have two hdds. 
hda0: 1.5TB
hda1: 400GB

There was no problem when I had used window xp and ubuntu 9.10 with grub.
Windows xp and Ubuntu had been installed on had1 with different partitions.
When I deleted the windows partition and tried to install windows 7, my computer was out of order.

During booting,, the following messages are showing on screen.

grub loading...
error: no such disk
grub rescue>

 I wanted to reset the whole system. So I deleted the all the partions on hda1(400GB).
Then I did re-partitioning the hda1(400GB) to re-install OS.

However, the same message as the above was displayed on the screen.

How can I fix this problems ?

Is there any way to remove grub boot loader?

I think it is possible to re-install the OS after I delete the grub.

GRUB2 is still in the MBR of hda1.  By default, we do not see the MBR of any  HD.

Go ahead and install win7 to the partition you want.  Win7 will overwrite the MBR with it's own bootloader ... which means you will not be able to access Ubuntu.  Don't fret.  Once you are happy win7 is running and updated, boot into your ubuntu liveCD and re-install GRUB.  That will overwrite the MBR again and install GRUB as the bootloader.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Post back errors or success.

Happy holidays :)

---

### Post by philinux on 2009-12-18
Or once win7 is installed use easybcd to boot ubuntu.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

