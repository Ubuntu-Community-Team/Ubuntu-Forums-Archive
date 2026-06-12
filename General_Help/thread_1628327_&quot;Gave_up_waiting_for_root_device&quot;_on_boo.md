---
title: "&quot;Gave up waiting for root device&quot; on boot"
date: 2010-11-22
forum: General Help
---

### Post by gunnarflax on 2010-11-22
I know this has problem has been discussed several times but it always seems to be on an older ubuntu version which doesn't have the same solution as mine. I'm currently running Ubuntu Desktop 10.10 x64.

When I'm trying to boot ubuntu I get this error message:
```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{my hard drive's uuid} does not exist. Dropping to a shell!

...

(initramfs)
```

I don't know what exactly it said since I copied the error message from another post here at ubuntuforums. But my boot device's UUID is:

9c4c7f41-fc46-4d58-ae1f-2c1eb06ffcfc

The problem only seems to occur when I have my LG CH10 Blu-Ray drive plugged into a SATA-port on the motherboard. When its just my Hard drive no error occurs. On the hard drive I have two partitions, one root and one swap and these are the only entries in my /etc/fstab. But when I run "$ sudo fdisk -lu" I get this:
```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1638

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  2909585407  1454791680   83  Linux
/dev/sda2      2909587454  2930276351    10344449    5  Extended
/dev/sda5      2909587456  2930276351    10344448   82  Linux swap / Solaris

```

So I think that the computer is recognizing the blu-ray drive as a second hard drive during boot and therefore an error occurs. When booted (by typing "exit" at the error message after I've waited a while) the blu-ray can't be ejected, which it can while in BIOS.

Here are different outputs I get when I've been searching for errors:
```

htpc@htpc:~$ sudo blkid -p /dev/sda1
/dev/sda1: UUID="9c4c7f41-fc46-4d58-ae1f-2c1eb06ffcfc" VERSION="1.0" TYPE="ext4" USAGE="filesystem" 
htpc@htpc:~$ sudo blkid -p /dev/sda2
/dev/sda2: PTTYPE="dos"
htpc@htpc:~$ sudo blkid -p /dev/sda5
/dev/sda5: UUID="c6643671-da4e-4292-8dfb-2de4399838f7" VERSION="2" TYPE="swap" USAGE="other" 

```
From the above lines my guess is that /dev/sda5 is optical drive but then again. I don't fully know what I'm doing, I'm a Linux rookie :)

I don't know what these lines mean but they were used during an [error research]("https://bugs.launchpad.net/ubuntu/+bug/518582") I found:
```

htpc@htpc:~$ sudo hexdump -s 0x410 -n 2 /dev/sda1
0000410 e468                                   
0000412
htpc@htpc:~$ sudo hexdump -s 0x410 -n 2 /dev/sda2
htpc@htpc:~$ sudo hexdump -s 0x410 -n 2 /dev/sda5
0000410 4eda                                   
0000412

```
No output done when running hexdump on /dev/sda2.

I hope someone can help me fix this! All help and answers are greatly appreciated!

Thank you!

---

### Post by gunnarflax on 2010-11-27
bump*

---

### Post by ajaborsk on 2010-11-27
Hi !

  Exactly the same problem here :

    Ubuntu 10.10 x64 (Athlon X4) and newsly installed CH10.

    It seems this is a SATA bus problem. If I wait for SATA bus to be ready (nearly one minute...) I can boot my linux, but not use the CH10.

    The problem can come from a race condition or random settings : I succeeded to use my CH10 one time (don't know how...)

   I'll try to investigate again.

Alexandre JABORSKA

---

### Post by ajaborsk on 2010-11-27
I just found a quick workaround : I plugged the CH10 in a SATA port that my motherboard can emulate as PATA port and activated this emulation. Works for me.

Alexandre JABORSKA

---

### Post by gunnarflax on 2010-11-27
Let me know if you make some progress! I will do my best too!

---

### Post by gunnarflax on 2010-11-28
> **ajaborsk said:**
> I just found a quick workaround : I plugged the CH10 in a SATA port that my motherboard can emulate as PATA port and activated this emulation. Works for me.

Alexandre JABORSKA

Does it still read blu-ray discs at good speeds?

---

### Post by gunnarflax on 2011-03-07
I gave up on this BD Combo reader and bought the [liteon iHOS104]("http://us.liteonit.com/us/index.php?option=com_content&task=view&id=274&Itemid=191") which the manufacturer even dare stating has linux support, and I can vouch for it. No problem what so ever. After a fresh install I no longer have any problems.

---

