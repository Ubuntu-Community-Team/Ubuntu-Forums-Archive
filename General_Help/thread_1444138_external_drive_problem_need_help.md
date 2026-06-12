---
title: "external drive problem need help"
date: 2010-03-31
forum: General Help
---

### Post by 37fleetwood on 2010-03-31
Hi, I'm hoping someone here can help. accidentally the usb plug on my WD "My Book" got halfway unplugged and I didn't notice it. when I rebooted it, it wouldn't read the drive. I tried using G Parted to repair it but no success, it just runs forever accessing the drive and never finishes. (I left it running an entire weekend and it didn't finish) the drive is formated ext3.
when I try to mount the drive in Ubuntu 9.10 it gives this error message:
[I]Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

strangely if I boot into Windows and use the ext driver I can access the drive just fine. is this something I can fix? if needed I can use Windows to do any repairs.

---

### Post by john newbuntu on 2010-04-01
Restart Ubuntu.  Plug in your USB and see if it detects it.

Using a terminal, create a directory under /media called usb.  Then run the command:
```
sudo fdisk -l
```
See if it is able to recognize the disk (usually /dev/sdb1 if you have only one internal disk)

Then run:
```
sudo mount -t ntfs-3g -o rw /dev/sdb1 /media/usb
```

See if this helps.  If not, type "dmesg" as soon as you insert the USB drive and post the output that you get in the terminal.  Also post the output of "lsusb". The will help the community in solving this issue for you.

---

### Post by 37fleetwood on 2010-04-01
your last bit of code has me mounting it ntfs? the drive is formatted ext3.
here is what I get if I run the first code you give:

[I]Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux[/I]

---

### Post by 37fleetwood on 2010-04-01
ok, I got it fixed! I moved as much as I could off the drive and finally G Parted worked. I noticed that it was reporting the wrong amount of used space before. so far it doesn't look like I've lost anything we'll see though.

---

### Post by john newbuntu on 2010-04-02
My bad  fleetwood.   I should have mentioned the right ext type.

---

