---
title: "2 hdd's displayed,only 1 installed?"
date: 2009-07-16
forum: General Help
---

### Post by christyd on 2009-07-16
hi.

when i run fdisk -l.i get.
[root@localhost ~]# fdisk -l

Disk /dev/sda: 8 MB, 8388608 bytes
8 heads, 32 sectors/track, 64 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table.

i have only 1 hdd installed and the way things are i
can't install any distro to my hdd.i am not very experienced
in computers and would would really appreciate any help.

regards.

christyd.

---

### Post by phillw on 2009-07-16
Hi,

bear with me - I just want to check I am correct .... brb in few minutes.

I think that hda is from your liveCD - I'm just going to boot with one !!!

---

### Post by prem1er on 2009-07-16
Are you running Ubuntu off of a flash drive? If you are the media gets mounted as a drive in linux. That is why you are seeing 2 "drives" (partitions).  If you were previously running windows, it may be a partition that was created during an old install that you couldn't see before.  Just because 2 devices are showing up does not mean it is detecting 2 HDs it looks like either (really small) flash drive, or a small partition that was created earlier.

---

### Post by phillw on 2009-07-16
Hi - deffo not something via the LiveCD - The previous poster had my next question - is there a USB drive plugged in ?

Phill.

---

### Post by christyd on 2009-07-16
hi phill.
thanks for getting back to me.there is only a usb keyboard and mouse connected.
i don't have much experience with computers.so please bare with me.im trying to install pce17os,as i ike the e17 desktop manager.when i try to install it,it installs to sda i think thats where grub bootloader is supposed to be? i have tried with various apps to delete sda but with no joy.i have also installed ubuntu and get a blank screen on boot.this is well beyond me?as is my hdd is of no use.i think i instaled virtualbox a while back.would that make a partition like sda?
regards christyd.

---

### Post by prem1er on 2009-07-16
Why are you posting here if you are trying to install a completely different distribution than what is supported here?  This is where you want to be.

[http://www.linfx.com/index.php?option=com_content&view=article&id=46:hungarian-pclinuxos-pce17os&catid=1:latest-news](http://www.linfx.com/index.php?option=com_content&view=article&id=46:hungarian-pclinuxos-pce17os&catid=1:latest-news)

---

