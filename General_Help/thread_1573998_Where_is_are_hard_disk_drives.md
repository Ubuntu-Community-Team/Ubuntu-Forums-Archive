---
title: "Where is are hard disk drives?"
date: 2010-09-13
forum: General Help
---

### Post by Snitz on 2010-09-13
I faced a problem earlier with the grub and the mbr which I didn't resolve.

After getting windows 7 dvd, attempting to fix the mbr. after doing the scan disk check, I couldn't read my hdd drives anymore. No C: and no D:

The only thing that it is detecting is the USB.
It's both on ubuntu and windows 7. I can't install any of them.

Where is my HDD? did it broke?

---

### Post by coffeecat on 2010-09-13
> **Snitz said:**
> Where is my HDD? did it broke?

Shortly after you switch on, press whichever key you need to get into the BIOS. Does the BIOS show your disk drives?

If it does, then boot up with a live Ubuntu CD. Open a terminal and post the output of:

```
sudo fdisk -l
```

That will show us whether there are any partitions on the drives and what they are.

If the BIOS doesn't show your drives, there is a hardware problem.

---

### Post by Snitz on 2010-09-13
> **coffeecat said:**
> Shortly after you switch on, press whichever key you need to get into the BIOS. Does the BIOS show your disk drives?

If it does, then boot up with a live Ubuntu CD. Open a terminal and post the output of:

```
sudo fdisk -l
```

That will show us whether there are any partitions on the drives and what they are.

If the BIOS doesn't show your drives, there is a hardware problem.
This is the output of "fdisk -l"

```
Disk /dev/sda: 2054 MB, 2054426624 bytes
64 heads, 62 sectors/track, 1011 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          812341      874508   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(812340, 26, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(874507, 47, 15)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *      109091      304576   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(109090, 32, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(304575, 21, 34)
Partition 2 does not end on cylinder boundary.
/dev/sda3          471160      954837   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(471159, 58, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(954836, 54, 35)
Partition 3 does not end on cylinder boundary.
/dev/sda4          534198      536296     4161564    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(534197, 43, 23)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(536295, 15, 22)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

I will check the BIOS now.

EDIT: no, I didn't see any hard disk drive letters in the BIOS.

---

### Post by coffeecat on 2010-09-13
I think we need to clarify what we are talking about.

> **Snitz said:**
>  I couldn't read my hdd drives anymore. No C: and no D:

and

> **Snitz said:**
> EDIT: no, I didn't see any hard disk drive letters in the BIOS.

"Drive" designation by letter (C:, D:, etc) is a Microsoft convention. A "drive" (by Microsoft's definition) can refer to a whole drive if this has one partition or a single partition on a physical drive which has more partitions on it. In your case, "drives" C: and D: could be separate partitions on a single physical drive, or could be separate physical drives. That's why I asked for the fdisk output - to see what you had, but back to that in a moment.

It's unfortunate that Microsoft chose to use the word "drive". It can very confusing. On a Linux forum it's best if you use the word "drive" only to refer to a physical drive.

Next - you won't see "C:" and "D:" in the BIOS. It will refer to the physical drives it can detect, not the partitions. What you will see is "drive 0" or "drive 1" or whatever, followed by the make and model number of the drive, plus the capacity in GB. DId you see anything like that. Because your fdisk output looks ominous?

OK - the fdisk output. It lists only one drive, only 2054MB in size - that's about 2GB. There is no way that is a hard drive that had previously had Windows 7 and Ubuntu on it. I guess that it is a USB flash drive. Did you have a flash drive plugged in when you did fdisk, or are you using a bootable USB drive for Ubuntu instead of a live CD? That would explain sda. So if your flash drive is the 2GB one (designated sda in fdisk), then fdisk is not detecting any hard drives. Which sounds serious.

---

### Post by Snitz on 2010-09-13
> Next - you won't see "C:" and "D:" in the BIOS. It will refer to the physical drives it can detect, not the partitions. What you will see is "drive 0" or "drive 1" or whatever, followed by the make and model number of the drive, plus the capacity in GB. DId you see anything like that. Because your fdisk output looks ominous?

I didn't see any hard disk (physical) detected, No partitions either.

> 
Re: Where is are hard disk drives?
I think we need to clarify what we are talking about.

Quote:
Originally Posted by Snitz View Post
I couldn't read my hdd drives anymore. No C: and no D:
and

Quote:
Originally Posted by Snitz View Post
EDIT: no, I didn't see any hard disk drive letters in the BIOS.
"Drive" designation by letter (C:, D:, etc) is a Microsoft convention. A "drive" (by Microsoft's definition) can refer to a whole drive if this has one partition or a single partition on a physical drive which has more partitions on it. In your case, "drives" C: and D: could be separate partitions on a single physical drive, or could be separate physical drives. That's why I asked for the fdisk output - to see what you had, but back to that in a moment.

It's unfortunate that Microsoft chose to use the word "drive". It can very confusing. On a Linux forum it's best if you use the word "drive" only to refer to a physical drive.

Next - you won't see "C:" and "D:" in the BIOS. It will refer to the physical drives it can detect, not the partitions. What you will see is "drive 0" or "drive 1" or whatever, followed by the make and model number of the drive, plus the capacity in GB. DId you see anything like that. Because your fdisk output looks ominous?

OK - the fdisk output. It lists only one drive, only 2054MB in size - that's about 2GB. There is no way that is a hard drive that had previously had Windows 7 and Ubuntu on it. I guess that it is a USB flash drive. Did you have a flash drive plugged in when you did fdisk, or are you using a bootable USB drive for Ubuntu instead of a live CD? That would explain sda. So if your flash drive is the 2GB one (designated sda in fdisk), then fdisk is not detecting any hard drives. Which sounds serious.


Yes, this is a usb stick.

So I guess my 1TB is really gone. But why? and do you think there's a chance to recover the data?

---

### Post by srs5694 on 2010-09-13
> **Snitz said:**
> So I guess my 1TB is really gone. But why? and do you think there's a chance to recover the data?

There are several possibilities. Broadly speaking, the drive could be bad, the data cable could be bad, or the disk controller could be bad. In this context, "bad" could be a hardware failure (something's friend on a board, for instance), or a simple disconnection (a power or data cable has come loose).

If you're comfortable with hardware modifications, it's not too difficult to work through these possibilities to determine where the fault lies; however, you may need additional hardware to do that. For instance, you might need to be able to swap in another drive or cable. The simplest problem to detect and correct is probably a loose cable. You can visually inspect your cables and, if you see no obvious problems, disconnect and reconnect them.

If you're not comfortable with hardware, your best bet is to take the computer to a repair center or get help from a friend who is comfortable with hardware repairs.

Ultimately, the only sort of problem that will prevent data recovery is failure of the hard disk hardware. If the disk won't spin up or is otherwise damaged, your only hope for data recovery is very expensive professional recovery services. A bad cable is easily replaced, and even if the hard disk interface (probably built into the motherboard) is dead, you can usually add a separate disk interface card to get everything working again.

---

### Post by coffeecat on 2010-09-13
> **Snitz said:**
> So I guess my 1TB is really gone. But why? and do you think there's a chance to recover the data?

Well - first things first. This could be a dead drive, but it might be something as simple as the data or power cable becoming disconnected from the drive inside the case. Open up the case and ensure that the two connectors are secure to the drive. Follow the ribbon cable from the drive to the motherboard and make sure the cable is securely plugged in at that end. (I'm presuming that this is a desktop and not a laptop because you have a 1TB drive.)

Another  possibilty to bear in mind: this could be the power supply unit failing, not the drive. When PSUs begin to fail they are sometimes capable of producing enough power for only some of the hardware.

Also - perhaps this is a motherboard hardware problem, not a hard drive problem. Perhaps the SATA controllers have failed. If you have a suitable USB hard drive enclosure (I'm guessing the drive is SATA because its a 1TB), you could put the hard drive in that and see if another computer can detect it.

But if this is a dead drive you  probably wouldn't be able to recover the data. Unless the BIOS can detect the drive, no OS can read the surface of the disc. Even with data recovery software, you would need a disc that is detectable. There may be data recovery specialists that can do something, but they would be expensive. 

If it is a dead drive, the fact that it is clearly fairly new is, unfortunately, not that surprising. Google did some research on their hardware records and found that  drives tend to fail after only the first few weeks to months, or after several years. If they survive the first couple of months they are likely to last a good long while. If your drive has indeed failed, then you must be unlucky to get one of the ones that fails early.

---

### Post by dcstar on 2010-09-14
> **coffeecat said:**
> 
.........
OK - the fdisk output. It lists only one drive, only 2054MB in size - that's about 2GB. There is no way that is a hard drive that had previously had Windows 7 and Ubuntu on it. I guess that it is a USB flash drive. Did you have a flash drive plugged in when you did fdisk, or are you using a bootable USB drive for Ubuntu instead of a live CD? That would explain sda. So if your flash drive is the 2GB one (designated sda in fdisk), **then fdisk is not detecting any hard drives**. Which sounds serious.

I seriously doubt that fdisk will see anything other than drives with valid partition tables.

Since the OP has clearly stated that he was mucking around with the MBR, I'd lay good money that he has basically corrupted the partition table.

Gparted will show any detected storage hardware, as for recovering a wrecked MBR/Partition Table, good luck......

---

### Post by coffeecat on 2010-09-14
> **dcstar said:**
> I seriously doubt that fdisk will see anything other than drives with valid partition tables.

fdisk does indeed see drives without partition tables. As a demonstration I've just zeroed out the whole of a "64" MB SD card which will have overwitten the partition table with zeroes. fdisk now gives me:

```
Disk /dev/sdb: 62 MB, 62783488 bytes
2 heads, 60 sectors/track, 1021 cylinders
Units = cylinders of 120 * 512 = 61440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```... which is very helpful information. The OP doesn't get this. There must be a hardware problem somewhere.

And anyway, why would fdisk not see drives without valid partition tables? From man fdisk:

> fdisk (in  the  first form of invocation) is a menu driven program for creation and manipulation of partition tables. It wouldn't be very good at its job if it couldn't.

---

### Post by baddnady23 on 2010-09-14
> Well - first things first. This could be a dead drive, but it might be something as simple as the data or power cable becoming disconnected from the drive inside the case. Open up the case and ensure that the two connectors are secure to the drive. Follow the ribbon cable from the drive to the motherboard and make sure the cable is securely plugged in at that end. (I'm presuming that this is a desktop and not a laptop because you have a 1TB drive.)


I would check this first.  Always start with physical connections.  I had the same issue once and I freaked because I thought something catastrophic happened to my computer.  In reality, the SATA cable somehow managed to work its way out of the connector overnight.

---

### Post by Snitz on 2010-09-14
Ok, this is going to be very weird news.

I woke up today, turned on my computer, booted into ubuntu livecd and voila, my hard disk is there. All the partitions and everything is still there. I don't know how or why but it is.

So I opened gparted, I flaged "sda2" which hold windows 7 as "boot", restarted and booted into windows 7 dvd, tried to redo the previous steps to restore the mbr, but none of them worked even though none gave me errors during process.
It's even detecting a backup image of the entire OS in windows 7.

When I restart, I get this message:
```
BOOTMGR is missing
```

What do you think?

---

### Post by coffeecat on 2010-09-14
> **Snitz said:**
> Ok, this is going to be very weird news.

I woke up today, turned on my computer, booted into ubuntu livecd and voila, my hard disk is there. All the partitions and everything is still there. I don't know how or why but it is.

Before you do anything else, go back and re-read srs5694's post and my post #7. You have an intermittent hardware fault. If you persist without solving this you risk corrupting the data on your TB drive. Open up the computer case now and check the cable connections to the hard drive. A loose cable is most likely, but this is important.

> **Snitz said:**
> When I restart, I get this message:
```
BOOTMGR is missing
```What do you think?

Once you've checked the cables, boot up with your Ubuntu live CD and go to this link:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or boot into Ubuntu on your hard drive if you can. I'm not clear from your posts whether you can. Now download and run the boot info script and post the contents of the RESULTS.txt file. That will give us the information I wanted from sudo fdisk -l. More importantly it will give information about the bootloaders. I suspect from the 'BOOTMGR is missing' message that some of grub has got installed to the Windows 7 partition, but the script will tell us exactly what is happening and we can take it from there.

---

### Post by Snitz on 2010-09-14
[QUOTE=coffeecat]Before you do anything else, go back and re-read srs5694's post and my post #7. You have an intermittent hardware fault. If you persist without solving this you risk corrupting the data on your TB drive. Open up the computer case now and check the cable connections to the hard drive. A loose cable is most likely, but this is important.[/QUOTE]

I opened it, there are no loose cables. Everything is connected.

I fixed the bootmgr error message but copying bootmgr from windows 7 dvd to C:\
```
copy bootmgr c:\
```

It worked. I am now able to enter my windows 7 without any problem.
But of course, there is no trace of ubuntu. Is there a way to add ubuntu to windows' startup?

---

### Post by mastablasta on 2010-09-14
you overwrote the GRUB (ubuntu's boot manager) with Windows boot manager.
 
regarding your hard drive - had a similar situation (a month old disk dissapeared) - cable was in place, but it turns out it was faulty and could even totally break my windows instalation. i managed to repair it once, and th eother time i reinstalled the OS. however problem persisted until i simply decided to change the cable with a new one. never had a problem since.

---

### Post by coffeecat on 2010-09-14
> **Snitz said:**
> But of course, there is no trace of ubuntu. Is there a way to add ubuntu to windows' startup?

You can only have the Windows MBR or grub stage 1 on the MBR of the hard drive. When you repaired the Windows MBR, you overwrote grub stage 1. Hence no grub menu.

You have three choices:

1 It is possible to use the Windows bootloader to boot Ubuntu. You have to edit a Windows configuration file somewhere within C:. I'm hazy about the details, have no experience of it, and when I saw it explained I decided not to even try. Grub works for me.

2 I believe there is something called EasyBCD which can control the boot process. I have no experience of it.

3 Repair grub by reinstalling grub stage 1 to the MBR. That would be my choice. Have a look here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

And don't forget to run sudo update-grub after you reboot into Ubuntu.

**Edit:** those instructions are for grub2. You haven't told us your Ubuntu version. If it's pre-Karmic or an upgrade from a pre-Karmic install then you will have legacy grub and the repair process is different.

---

### Post by Snitz on 2010-09-14
I downloaded the latest version of Ubuntu: **ubuntu-10.04.1-desktop-i386**
Do I need grub or grub2?

I'm really hesitating to reinstall the grub, I've been trying this method for days with no results.
But I will give it one more try.

I went to the link you provided.

1. Log into ubuntu live cd
2. In the terminal: sudo mount /dev/sda6 /mnt
3. sudo grub-install --root-directory=/mnt/ /dev/sda

Is this correct?
In step 3, why isn't it /dev/sad6 (the number on which ubuntu is installed?)

---

### Post by Snitz on 2010-09-14
I am back where I started. Grub installed, showing Ubuntu only and another copy of dysfunctional ubuntu on sda5 and no trace of windows7.

---

### Post by coffeecat on 2010-09-14
> **Snitz said:**
> I am back where I started. Grub installed, showing Ubuntu only and another copy of dysfunctional ubuntu on sda5 and no trace of windows7.

I've seen this problem reported in other threads: grub2 failing to detect the presence of Windows 7. This doesn't affect all people - grub2 picked up Windows 7 on the machine I'm posting from - but it's clearly a problem that crops up for some.

You could search the forum for this and see whether anyone has a fix. There must be a reason why grub2 sometimes doesn't see the Windows partition.

Alternatively, you can add a menu entry yourself. What you need to do is explained in the community grub2 page:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Essentially it involves making the file /boot/grub.d/40_custom executable and adding your own custom stanza and then running update-grub. If you need any help with this it would be better to start a new thread. If you do, include the RESULTS.txt file from the boot info script I pointed you to. It provides the information needed to create a custom stanza.

**Edit:** it seems as though you already have - a day ago. :|

[http://ubuntuforums.org/showthread.php?t=1573274](http://ubuntuforums.org/showthread.php?t=1573274)

I have nothing more to add. It seems you are being helped on the other thread.

---

### Post by Snitz on 2010-09-14
It worked, it worked!
I tried this command for a change and it detected windows 7

```
sudo aptitude install grub-pc
```

Now on the boot loader, I'm able to choose between ubuntu and windows 7.
This is great. However, I'm having problems with ubuntu, sometimes when I select it, it just freezes and I have to restart for another attempt to enter it.

---

### Post by srs5694 on 2010-09-14
> **Snitz said:**
> Now on the boot loader, I'm able to choose between ubuntu and windows 7.
This is great. However, I'm having problems with ubuntu, sometimes when I select it, it just freezes and I have to restart for another attempt to enter it.

Intermittent problems like you're having are often caused by loose connections. It's possible that one of your cables is loose or defective and is failing intermittently. I know you said you've *checked* your cables, but if you haven't already do so, I recommend *completely unplugging* them (unplug the data cable from both the hard disk and the motherboard ends) and plugging them back in again. If that doesn't help, try replacing the hard disk's data cable with a new one, and if you have any spare hard disk power cables from your power supply, use a different one than what you're using. You can also try plugging the hard disk's data cable into a different connector on the motherboard, if you have any to spare. (If this is an old PATA system or if you have multiple hard disks, this could change the way the system boots and require adjusting or re-installing the boot loader, though. This change should not require such tweaks a 1-hard-drive SATA system.)

---

