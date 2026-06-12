---
title: "Ubuntu installation won't boot"
date: 2011-02-07
forum: General Help
---

### Post by Taxile on 2011-02-07
Good evening all.  This is first post and I am brand new to Linux / Ubuntu so please be patient.

I have an old (2003) fully functioning PC that runs XP and I used it to install Ubuntu on to 2 separate HDDs that are intended to be put into other older computers that I am building for friends from spares.

The PC's own HDD was removed during the install processes.  I replaced it with the first of the other HDDs, installed Ubuntu thereon, rebooted to confirm the successful install, then repeated the process with the second of the other HDDs.

I subsquently replaced the original untouched HDD (XP only) and now it won't boot although it is recognised in the BIOS.  I replaced it with the first of the Ubuntu HDDs and it wouldn't boot either (it would boot partially to the Busybox menu).

I then replaced that HDD with the second Ubuntu HDD and it worked fine.  

This working HDD - lets call it Ubuntu 2  - is the one that was most recently set up and I suspect that is the root of the answer to my dilemma.  It appears to me that the HDD installation also affects the computer itself, in that the HDD perhaps mounts itself to the PC - and given that none of the other HDDs were connected at the same time (when Ubuntu was installed) they are effectively now 'unmounted'.

If anyone can provide me with the solution as to how i get the original (XP - sorry!) HDD back up and running I would be very grateful.

I also assume from my problem that the Ubuntu installs will be useless on other computers - ie that the HDD has to be in the computer in which it will be used.  If anyone has any comments on this point, again I would be grateful.

For the record, I am very impressed with what little I have seen of Ubuntu so far and indeed from what I've read previously when reading up beforehand.  I've been particularly impressed with the whole Linux community's eagerness to help each other, although I did not anticipate that I wuld be leaning on you all so quickly!  Nevertheless, I have no doubt my problems are easily rectified with the appropriate advice from someone more knowledgeable (ie the entire Linex community outside of me...) and I look forward to learning from your anticipated words of wisdom.

Thank you all

---

### Post by quadproc on 2011-02-07
> **Taxile said:**
> 
I subsquently replaced the original untouched HDD (XP only) and now it won't boot although it is recognised in the BIOS.  I replaced it with the first of the Ubuntu HDDs and it wouldn't boot either (it would boot partially to the Busybox menu).

I then replaced that HDD with the second Ubuntu HDD and it worked fine.  

This sounds like you might have a UUID problem.  Since I don't know how the disks were partitioned and formatted, I have to guess.  Also, I have to guess at what you mean by "won't boot" - I am suspecting that you get a grub menu but that grub fails to load the OS.

A UUID is a unique 128 bit number that is assigned to a partition when the partition is created.  That number is often used by other parts of the system to identify that particular disk partition.  For example, here is something from my /etc/fstab:
```
# / was on /dev/sda9 during installation
UUID=71059336-6d53-4273-ad4e-49dd1a223ed4 /               ext3    errors=remount-ro 0       1
```This tells the kernel that it should use the partition identified by the UUID as root (i.e., "/").

You can get a list of UUIDs from a system by booting from the Live CD and, in a terminal, typing in
```
sudo blkid
```Anyhow, if you could furnish some more details it would be helpful.

quadproc

---

### Post by Taxile on 2011-02-07
The simple point seems to be that the boot operation failed to recognise the XP drive or the first created Ubuntu drive, because they were not part of the system when I did the final Ubuntu OS install (on the 3rd drive).

As I said, I'd removed the XP drive and replaced it with each of the other drives in turn whilst I installed Ubuntu onto them.  I then put the XP drive back in on its own (the other Ubuntu drives ultimately being intended for other computers).  

I assumed the XP drive would work as normal when I put it back in on its own, but I was unaware that installing Ubuntu woud alter the the system boot settings.  I susbequently tried all 3 drives individually and the only drive that would boot to its OS was the most recently created Ubuntu drive.  

The norm in my eyes (ie with experience of only using Windows OSs...) was that the system would simply boot to whichever drive was specified in the BIOS, regardless of its OS or whether it was a newly introduced drive etc.  I did not expect that the boot order would essentially now be looking for non-existent operating systems on non-existent drives.

I did some research on altering the grub boot settings but the advice did not work for me.  Instead, I did a reinstall of Ubuntu on one of the secondary drives whilst the XP drive WAS connected and now I have the dual boot / dual HDD/OS option.  

Btw, my original intention was to keep it solely as an XP PC but it makes  little difference whether I do or not.  The only reason I intended keeping it as an XP PC is because it has MS Office 2007 etc and it seems preferable to use XP rather than emulating with Wine or whatever.

In reality though, I never use the PC anyway apart from for testing and setting up other PCs for friends from spares and old parts picked up from the street (literally).  I used to install them with XP but only because I had various spare licences that are now used up.  I'll be using Ubuntu in future so it makes sense that I have it on my testing system.

In time, when I come to remove the Ubuntu drive for putting it into one of the PCs I'm renovating, I'll do another install to partition the current XP drive with Ubuntu.

I use Office 2007 and various non-Linux software on my main PC / laptop for my business (I run an accountancy firm from home), so Bill Gates wil continue to be babysitting those systems for the time being at least.  I hope that doesn't make me incur the wrath of my new found friends in the Linux community :-) 

Cheers

---

### Post by quadproc on 2011-02-09
> **Taxile said:**
> 

I assumed the XP drive would work as normal when I put it back in on its own, but I was unaware that installing Ubuntu woud alter the the system boot settings.
If I understand correctly, you had physically removed all but one disk drive (including any USB drives or similar devices) when you did the install.  Given this, it is not possible for Ubuntu to have changed anything on the other disks and they should still function as they did before.

However, if you had a USB stick in the system during installation, then you could very well have installed grub on the stick, and grub would expect to find a particular hard disk to use when booting.  Thus, my comment about UUIDs.
> 
The norm in my eyes (ie with experience of only using Windows OSs...) was that the system would simply boot to whichever drive was specified in the BIOS, regardless of its OS or whether it was a newly introduced drive etc.  I did not expect that the boot order would essentially now be looking for non-existent operating systems on non-existent drives.Actually, your system will boot from whatever *device* is specified in the BIOS setup, regardless of what bootloader or OS is on that device.  In the case of Ubuntu/grub, the install will create a tiny program in the master boot record of the specified device and that tiny program will execute when the BIOS has finished with its startup stuff.  That tiny program (grub) will present you with a choice of which OS you would like to use, and will load that.  If there is only one choice then grub will not ask you for which OS to load, it just loads the only one that it knows about.

When grub is creating its list of candidates to load, it will examine everything that it can to see if there might be runnable operating systems on them.  If so, it includes them on the list.

Multibooting with Windows works a little differently.  Microsoft takes control of your system and looks for other operating systems which it attempts to disable or hide.  Consequently, your life is much easier if you install Windows first and then install Ubuntu because the Microsoft OS will not be trying to throw away Ubuntu, at least not straight off.  In my experience, Windows Vista decided that there was "something wrong" with my Ubuntu-containing disk, and "fixed" the disk.  I then had to run fsck on the disk to repair the damage done by Vista.

Also, because of the "it's my football" design of Windows, you normally want to use a chainloader to boot Windows.  This is normally taken care of by grub and you don't need to do anything in particular.
> 
In time, when I come to remove the Ubuntu drive for putting it into one of the PCs I'm renovating, I'll do another install to partition the current XP drive with Ubuntu.You should not *need* to have any Microsoft on the system anywhere.  For example, I had a system disk failure a few weeks ago so I bought a replacement drive, brand new and with no OS on it, put that into the system, booted from the Live CD, partitioned the disk the way I wanted it, and installed the system into one of the new partitions.  That means that this system has never had any Microsoft on it.

quadproc

---

### Post by oldfred on 2011-02-09
If this is an older computer, is it IDE/PATA? If so then BIOS may control less of boot process than newer computers and rely on primary master. Or which hard drive has the jumpers set to be the primary master, or if cable select how it is plugged into the cable and still what jumpers are set on hard drive.

Did you change any jumpers or the location you plug into the cable(s)?

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

