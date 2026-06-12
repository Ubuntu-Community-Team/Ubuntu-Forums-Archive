---
title: "Grub boot loader, load windows by uuid"
date: 2009-09-15
forum: General Help
---

### Post by lordofduct on 2009-09-15
Ok I've googled for the answer to this, but everyone writes their windows boot entry in /boot/grub/menu.lst using the (hd#,#) instead of by uuid when writing their windows boot entries.

Now let me explain what is up here.

I have Windows 7 running on a second hard drive (completely different drive from the drive I have Ubuntu on).

Ubuntu is my primary system, I installed one of those beta or what nots of 7 to check it out. The drive Ubuntu is on is the first drive in the list of drives.

Windows 7 though exists in sata slot 5. Sometimes it's viewed as the second slot, in which hd(1,0) works fine. BUT I also have a removeable esata external hard drive. Which when attached it takes the second position and the Windows 7 then should be (hd2,0).

Now of course I can just make sure the external drive is either off or not connected when booting. But sometimes (like when my girlfriend turns on the computer) this isn't so apparent and just make things frustrating.

Ubuntu's entries in my menu.lst are as uuid, which works fine. But if I check the UUID of windows 7, and put that in for it's entry, it fails to boot. It only works if I use (hd#,#)

here's my menu.lst (relavent part only):

```

## ## End Default Options ##
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		50ff4d78-aa1b-4db0-9af0-44fb796bd359
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=50ff4d78-aa1b-4db0-9af0-44fb796bd359 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

... omitted different kernel entries

title		Ubuntu 9.04, memtest86+
uuid		50ff4d78-aa1b-4db0-9af0-44fb796bd359
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		windows 7 beta (Loader)
#uuid		B00458AD045877F4
root		(hd1,0)
makeactive
chainloader +1

```

---

### Post by joehillen on 2009-09-21
I am having this same issue.

---

### Post by lordofduct on 2009-10-13
I'm bumping this, see if it can get more exposure

---

### Post by frogitts on 2009-10-28
Also having the same issue.

---

### Post by GilbertEvanG on 2009-10-30
I am having this same problem. I have confirmed that it is the windows record of menu.lst that is messing things up. If I comment out the windows record, so I only have a record for ubuntu using UUID, I can boot up fine with my external hard drives plugged in. But when the windows entry is present with its (hdx,x) deal, I get a grub error (22?).

---

### Post by avada on 2009-11-12
I'm startintg to think it's impossible to use uuid's for windows. This topic was the most relevant from anything I found.

---

### Post by Objekt on 2009-11-15
Ack.  I was just wanting to set up dual-boot on my new netbook using only UUIDs, but I guess it's impossible.

I have Kuki Linux as my main OS on the netbook, but I also installed (via an SD card, which was a neat trick in itself) the 32 bit Windows 7 RC to mess around with.  
Since I frequently have various different storage devices attached - SD card, external HDD, USB flash memory stick - in different combinations, trying to use the old (hdx,y) nomenclature is just asking for trouble.  But, there appears to be no way to make GRUB load the Win 7 bootloader by pointing it to the Win 7 boot volume's UUID.

I guess until someone figures out a way to load Windows using UUID references, I'm stuck playing trial-and-error to eventually find the magical X and Y for the (hdX,Y) statement.  Which will, of course, change if I happen to have the external HDD plugged in at startup.  Argh.

---

### Post by MaxIBoy on 2009-11-15
As far as I know, the only way to boot Windows from GRUB is to chainload Windows' native bootloader.

---

### Post by Mark Phelps on 2009-11-15
> **MaxIBoy said:**
> As far as I know, the only way to boot Windows from GRUB is to chainload Windows' native bootloader.

That's correct.  All GRUB is doing is pointing to a partition and starting the MS Windows boot loader it finds in that partition.

After that, the MS Windows boot loader takes over.

---

### Post by oldfred on 2009-11-15
I know it is a kluge but you can just put two entries into your menu.lst for old grub or 40_custom for grub2. You know whether you have your portable plugged in or not and can say in the title which is mapped from disk 1 and which is disk 2.

Something like:

title        Microsoft Windows 7 without Portable
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

title        Microsoft Windows seven with Portable
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

---

### Post by avada on 2009-11-22
> **Mark Phelps said:**
> That's correct.  All GRUB is doing is pointing to a partition and starting the MS Windows boot loader it finds in that partition.

After that, the MS Windows boot loader takes over.

But it could find the partition by uuid instead of the hd(x,y) stuff, couldn't it? And then load the win7 bootloader.

---

### Post by avada on 2009-12-09
I installed 9.10 and I got grub 1.97 (but it seems like grub2)

In the grub.cfg this was generated for the windows enty:

```

menuentry "Microsoft Windows XP Professional - magyar (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a668ae3068adff65
	drivemap -s (hd0) ${root}
	chainloader +1
}

```
So does it mean that it uses uuid to find the partition?
The identifier after --set is the same in fstab (in upper case). Although I don't know what does the "set root=(hd0,1)" line does then. In menu.lst something like that pointed to the partition that had windows on it if I remember correctly.

---

### Post by bumanie on 2009-12-09
Grub 2's numbering has changed - grub-legacy had first hard drive as 0 and first partition as 0 - grub 2 has first hard drive still as 0, but first partitions are no longer 0, but they are now 1, hence (hd0,1) - with grub-legacy would have been (hd0,0). To find device names and designations to match with a UUID > sudo blkid 

---

