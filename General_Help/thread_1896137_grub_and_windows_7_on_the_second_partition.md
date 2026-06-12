---
title: "grub and windows 7 on the second partition"
date: 2011-12-16
forum: General Help
---

### Post by cong06 on 2011-12-16
I started off with ubuntu (sda1) and a swap partition (sda2).

I wanted to add windows, but instead of wiping the whole hard drive, or installing off a cd, I decided to backup and restore my windows 7 partition using dd, into a third partition:

```

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000bb5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   159199231    79598592   83  Linux
/dev/sda2       242102270   250068991     3983361    5  Extended
/dev/sda3       159199232   242100223    41450496   83  Linux
/dev/sda5       242102272   250068991     3983360   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 4078 MB, 4078960640 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7966720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a8994c4

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```
(sd3, my windows partition, is an ntfs partition according to gparted)


Then I ran update-grub:
```

isaac@bohr:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-13-generic
Found initrd image: /boot/initrd.img-3.0.0-13-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
done

```

When I boot up, Windows 7 shows up in the grub list, but choosing it sends me to a screen with a blinking white cursor in the top left corner.

I imagine there's something else I need to do on my windows partition to make it bootable... I don't want to spend the time to move Linux to the end of the drive, and I really don't want to have to wipe everything and start over.

---

### Post by Mark Phelps on 2011-12-16
According to what you posted, sda3 is formatted for Linux.  Win7 needs Windows-formatted partitions -- NTFS preferably.

---

### Post by cong06 on 2011-12-16
Great theory.
I had initially created the partition as ext2/3, and then dd'd the ntfs partition into it.

I deleted the partition, and recreated it ntfs before I dd'd it over again:
```
Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000bb5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   159199231    79598592   83  Linux
/dev/sda2       242102270   250068991     3983361    5  Extended
/dev/sda3       159199232   242102269    41451519    7  HPFS/NTFS/exFAT
/dev/sda5       242102272   250068991     3983360   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 4078 MB, 4078960640 bytes
255 heads, 63 sectors/track, 495 cylinders, total 7966720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04335a9b

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
```

I have the same issue, though. A white cursor on a black screen.

---

### Post by N00b-un-2 on 2011-12-16
I hate to be the bearer of bad news, but Windows can not be restored onto a partition the way Linux can.  It sounds like at the absolute minimum your NTLDR is broken because of what you did, not to mention the fact that it will probably never work again because of how the registry works.  There may be a chance you can run a Windows install disk and do a start up recovery, but I can pretty much guarantee it will fail.  Windows is specifically designed NOT to be portable like that to prevent people from doing something like say... cloning their friend's hard drive image of Windows 7 Ultimate onto another computer that has Starter on it.  One copy per license, one license per machine and they spend quite a bit of effort to keep it that way.  If you want to move Windows your only option is to back up your files, do a fresh install and then copy your files over.

---

### Post by cong06 on 2011-12-17
*sigh* alright. I guess at least now I have closure to that dilemma.

Fortunately I didn't have anything important on the partition, and even if I did it's still mountable.

Linux spoils me.

---

### Post by N00b-un-2 on 2011-12-22
Linux does not spoil you, Linux is computing the way it should be.  Windows enforces ridiculous unethical restrictions on users for the sake of making money.  Even an OSX install can be cloned onto another hard drive without issues.  The Microsoft mentality of "You don't own the software you paid for, you own a license to use our software on the hardware we specify" is one of the main reasons I left Windows.

---

### Post by rjf1 on 2011-12-22
Doesn't Windows have to go on the 1st partition of the drive?

---

### Post by oldfred on 2011-12-22
Windows has to boot from a primary NTFS partition (in Linux sda1 thru sda4) with the boot flag.

Some have installed both XP in a primary and then Windows 7 in a logical and it works. Not knowing the Windows 7 boot files are really in the XP partition as it is the primary with the boot flag, they delete XP and wonder why 7 stops booting.

More info here:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Mark Phelps on 2011-12-22
You're certainly not alone HERE in strongly disliking Windows ... but some of your claims are off-base ...> **N00b-un-2 said:**
> Windows enforces ridiculous unethical restrictions on users for the sake of making money.
NOT allowing you to make illegal copies is "unethical"? MS is a Commercial company -- and ALL such companies exist to "make money" -- even Apple computer! >  Even an OSX install can be cloned onto another hard drive without issues.  And ... so can a Windows install.  I've cloned my install several times, each time to upgrade to a larger, faster drive, and most recently, to an SSD. And in NONE of these instances did I have any "issues".
>  The Microsoft mentality of "You don't own the software you paid for, you own a license to use our software on the hardware we specify" ... Funny, I don't ever recall MS specifying what hardware on which I could install Windows.

As to "migrating" it, while I admit MS doesn't make it easy, there are several third-party products that will not only allow you to "migrate" a Windows install to a different PC, they also allow you to "restore" a Windows install made on one PC to another PC with completely different hardware.  And, if the new install refuses to activate, a quick 5-minute FREE phone call to MS Tech support fixes that.

I don't have a problem with folks disliking MS, but if we're going to BASH them, at least lets be truthful in the claims.

---

### Post by cong06 on 2011-12-22
> **oldfred said:**
> Some have installed both XP in a primary and then Windows 7 in a logical and it works. Not knowing the Windows 7 boot files are really in the XP partition as it is the primary with the boot flag, they delete XP and wonder why 7 stops booting.

I think I'm alright in that respect, though aren't I?
Grub boots off the first partition, and then can boot onto the windows 7 partition that I have.

I guess I haven't quite figured out what windows is missing for the boot to actually work...

> **Mark Phelps said:**
> I've cloned my install several times, each time to upgrade to a larger, faster drive, and most recently, to an SSD. And in NONE of these instances did I have any "issues".

So what did you do differently than me?

---

