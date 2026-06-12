---
title: "Boot drives gone"
date: 2012-05-11
forum: General Help
---

### Post by Bart123456 on 2012-05-11
Hello,


Yesterday I've received this message when booting up:

[I]mount: mounting /dev/disk/by-uuid/04aa3697-7bc0-45b5-b86a-77a1e6534bd5 on  /root failed: invalid argument
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /dev on /root/sys failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init fount.  Try passing init= bootarg.[/I]

I found the solution for this via live cd:
[I]sudo fdisk -l
sudo fsch/dev/sda5[/I]

And everything worked properly, and I just shut down my computer. Today when I wanted to start, My computer could not detect any bootdrive at startup (only my usbdrive with the live cd. I've tried to boot-repair, but It could not find anything.

when entering sudo fdisk -l this time I get:
[I]Disk /dev/sda: 8000 MB, 8000110592 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15625216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00053028

   Device Boot      Start         End      Blocks   Id  System[/I] [I]
/dev/sda1   *          63    15625196     7812567    b  W95 FAT32[/I]

linux was installed on sda5, but this is gone, just like windows

Here you can find the info from boot repair
[http://paste.ubuntu.com/982010/](http://paste.ubuntu.com/982010/)


I''ve used 12.04 since it's available without problems
I have a dual boot with windows Vista, but it can't find it either
Windows is via C drive, Linux via another internal hard disk  (D drive)

Anybody could help? (PS. I'm a noob)

Thanks,
Bart

---

### Post by cmont899 on 2012-05-11
Sounds like your hd failed. If you go into the BIOS do you see the drive listed? Have you confirmed that none of your hard drive cables are loose/unseated?

---

### Post by Bart123456 on 2012-05-11
> **cmont899 said:**
> Sounds like your hd failed. If you go into the BIOS do you see the drive listed? Have you confirmed that none of your hard drive cables are loose/unseated?

Drives are not listed into the BIOS,I've checked the cables but everything seems ok

---

### Post by cmont899 on 2012-05-11
Time to buy a new drive. If you need data there are companies that you can send the drive to that can recover but it's pricey.

---

