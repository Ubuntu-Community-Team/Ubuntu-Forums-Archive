---
title: "&quot;Gave up waiting for root device&quot;"
date: 2009-12-17
forum: General Help
---

### Post by tc33 on 2009-12-17
Whenever I try to load up my laptop, I get the message:

"Gave up waiting for root device. Common problems:
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missingm odules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/87c25b29-3c55-4dd2-bcd0-5faf85255124 does not exit. Dropping to a shell!

Busy box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)"

Please note that I'm a complete beginner, so maybe keep the language... simple?

[P.S. I was using 9.10 Karmic Koala, if that helps)

Thanks!

---

### Post by audiomick on 2009-12-17
Hallo.
I'm afraid I can't help more than to say that I have seen a few posts in the last couple of weeks from people who seem to have the same problem. 

The UUID bit
> ALERT! /dev/disk/by-**uuid/87c25b29-3c55-4dd2-bcd0-5faf85255124** does not exit. Dropping to a shell!
is a type of pointer to where the partition is which the system should boot from. The boot loader, grub2 if you are using Ubuntu 9.10, before that grub, is looking in the wrong place, which is why it says the partition doesn't exist. If can be repaired.

If you don't get any help within a day or so, "bump" the thread, i.e. put in another post to get it back up to the top of the list. Lots of people just write bump.

---

### Post by lmarmisa on 2009-12-17
[I]ALERT! /dev/disk/by-uuid/87c25b29-3c55-4dd2-bcd0-5faf85255124 does not exit. Dropping to a shell!

[/I]This message means that a system partition (probably the root partition) cannot be mounted because its UUID has changed or does not exist anymore.

[http://en.wikipedia.org/wiki/Universally_Unique_Identifier](http://en.wikipedia.org/wiki/Universally_Unique_Identifier)

Try to type these commands (in the Busy Box shell or, better, opening a terminal running a Ubuntu Live CD):

```

sudo fdisk -l

```This command will list the detected partitions.

Busy Box shell
```

cat /etc/fstab

```LiveCD
```

sudo mount /dev/sda1 /mnt      # Change to the correct device if root is not /dev/sda1 (according to output of fdisk -l)
cat /mnt/etc/fstab

```This command will list the automount instructions at startup.
```

sudo blkid
 
```This command will list the UUIDs of the detected partitions. Compare with fstab.

Could you post the outputs of these commands for helping to fix your problem?. If you  run a Live CD, use copy & paste to Firefox.

---

### Post by tc33 on 2009-12-18
Thanks for helping!

I got:

/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="87c25b29-3c55-4dd2-bcd0-5faf85255124" TYPE="ext3"
/dev/sda5: UUID-"7ee41a36-c09d-472e-a087-78bfe6948c37" TYPE="swsuspend"

---

### Post by lmarmisa on 2009-12-18
I suppose that you have posted the output of the blkid command running the *Busy box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)*. Right?.

The UUID of the device /dev/sda1 seems correct but I can not see any reference to the swap partition.

Could you post the output to the command **fdisk -l** or sudo **fdisk -l**.

Best regards,

Luis

---

### Post by dcstar on 2009-12-18
> **tc33 said:**
> Whenever I try to load up my laptop, I get the message:

"Gave up waiting for root device. Common problems:
**- Check rootdelay= (did the system wait long enough?)**
- Check root= (did the system wait for the right device?)
- Missingm odules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/87c25b29-3c55-4dd2-bcd0-5faf85255124 does not exit. Dropping to a shell!

Busy box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)"

Please note that I'm a complete beginner, so maybe keep the language... simple?

[P.S. I was using 9.10 Karmic Koala, if that helps)

Thanks!

Possibly something in your hardware is taking a bit too long to settle before Ubuntu tries to access it - do you have any BIOS settings with hard disk delays set?

---

### Post by audiomick on 2009-12-18
> **dcstar said:**
> Possibly something in your hardware is taking a bit too long to settle before Ubuntu tries to access it - do you have any BIOS settings with hard disk delays set?

While you're at it, try turning off all the fast start stuff in the BIOS. It helped me with start problems. I have samsung discs that seem to just take a while to spin up. It also doesn't hurt to make sure all the cables are plugged in properly.

---

### Post by RichTB on 2009-12-21
I've got a similar problem with Ubuntu 9.10 kernel 2.6.31-16-386

The boot sequence ends with the following

!/scripts/local-top...
Waiting for root file system
Done
Gave up waiting for root device.  Common problems:
Boot args (cat /proc/cmdline)
   Check root delay = (did the system wait long enough?)
   Check root = (did the system wait for the right device?)
- Missing Modules (cat /proc/modules: ls /dev)
Alert! /dev/disk/by-void/46c7586c-82c8-49af-8309-612beaa80d55 does not exist.
Dropping to a shell!

Busy Box v.1.13.3 (ubuntu 1:1.13.3-1 ubuntu 7) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)


I've been using Ubuntu for years on this h/w without any problems.  It's clear the the boot process is not completing, but why and what to do about it.  Any clues?

---

### Post by Psyclon on 2010-10-07
I get the same thing. I'm running Ubuntu 10.10 now, but had the same problem with the last version. 
 This is what I get:

Me:~$ sudo blkid
/dev/sda5: UUID="41e687a7-ebcc-4444-956d-8f5235d0e0f4" TYPE="swap" 
/dev/sda1: UUID="a64bffdb-b195-4c14-87fc-decf572e572d" TYPE="ext4" 
Me:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab17b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37808   303689728   83  Linux
/dev/sda2           37808       38914     8879105    5  Extended
/dev/sda5           37808       38914     8879104   82  Linux swap / Solaris


If anyone can help, lemme know.

---

