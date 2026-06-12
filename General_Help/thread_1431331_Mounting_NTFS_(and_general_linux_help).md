---
title: "Mounting NTFS (and general linux help)"
date: 2010-03-16
forum: General Help
---

### Post by BananaPeal on 2010-03-16
Hello Everyone!

My Windows bootloader disappeared and its repair facility is telling me the NTFS volume is corrupt, so I'm switching over to Ubuntu for now!

I can mount that ntfs drive using: sudo mount /dev/sdb2 /media/windows

This works, except that I can't modify files on the drive as my normal user.

I tried changing permissions on subfolders of the drive using: 
gksudo nautilus 
and then using the GUI to change ownership to my username.

The permissions switched back to root as soon as I made the change though! No error message!

I imagine I can circumvent this by mounting to my home directory using simply
 mount dev/sdb2 ~username/windows

Does it matter where I mount the drive to? /media/ seems like a good choice since that's where all the drives are but I have this permission trouble. 

Does it matter? Performance issues? I imagine Linux doesn't break like windows over time if things aren't where they should be...

I'd welcome any thoughts/opinions on the matter!

---

### Post by coffeecat on 2010-03-16
> **BananaPeal said:**
> I'd welcome any thoughts/opinions on the matter!

A couple.

If the NTFS volume is corrupt it needs to be repaired using the Windows chkdsk tool. NTFS is a Windows filesystem. Although there are Linux tools for doing some maintenance of NTFS, they are not as comprehensive as chkdsk. Indeed the 'ntfsfix' (a command line utility) manual says:

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.Is the corrupted volume a Windows C: "drive"? If so you really need to take the disc out, put it in a USB enclosure and chkdsk it from another Windows installation before you try to read it with Linux or you may cause further filesystem corruption.

Second point: you can't change permissions on an NTFS drive because NTFS (being a Microsoft filesystem) doesn't support Linux/Unix permissions! When you mount an NTFS partition with the Linux ntfs-3g driver everything appears to be owned by root - it's a function of the way ntfs-3g works - but you should be able to access it read-write as an ordinary user.

The problem may be that you're mounting from the command line. You may need to chown the mountpoint or add some mount option. But far better though is to simply automount it from the GUI by going to the Places menu. One click, your password, and you're done. If you do that you will be able to read/write to it. If you can't, something is wrong with the filesystem.

Which brings us back to my first point. Perhaps the filesystem corruption is preventing you from reading it. If you can get an USB enclosure and access to another Windows system, do a chkdsk first.

---

### Post by Serpher on 2010-03-16
First of all it doesn't matter when you mount your partition. You can even mount it in a directory with things already in it, it's just those files and directories would be unavailable while it's mounted, including system files in places like /etc/ so I wouldn't mount it there. Second of all, UNIX file permissions don't do anything on NTFS partitions. Although you don't get any errors, nothing actually happens. If you run the command 'ls -a <file>' where <file> is the file or directory you're checking, you'll notice the permission is probably something like 'd---------' or just '----------'. It sounds like the portion of your NTFS partition that manages file tables etc it corrupted. I would just run chkdsk or if you don't feel like hunting around for/burning a Windows disc, just install and run ntfsdisc. Since it seems you're new to Linux you can install ntfs disc by going into the terminal and typing 'sudo apt-get install ntfsdisc' or go to Applications --> Software Center for a GUI tool.

---

### Post by mikewhatever on 2010-03-16
BananaPeal, what version of Ubuntu are you running? Is it installed, or is it running from a live media like cd/usb?

---

### Post by BananaPeal on 2010-03-16
Mike: I'm running 9.10 since windows died... seeing if I can use it day-day.

Thanks for your tips it's really comforting to understand what's happening for a change!

Long story short: it is indeed a botched installation after my original windows HDD died, the bootloader got confused and wouldn't start the new windows on the new disk. The bootrec tool told me the NTFS was corrupt when i tried fixing the boot files.

I'll try running the windows install cleanly again after moving my files over and hopefully this page will get back my dual-boot setup:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I was using the command line to automatically mount the drive on startup by running the command out of "startup appliations". 

Is there a good resource on how linux (ubuntu in particular) is organized/common commands, and ways of doing stuff or do most people just learn by doing? 

I'm starting to get the hang of it but sometimes stuff just takes forever.

Thanks again for your help! I'll let ya know how it goes!

---

### Post by coffeecat on 2010-03-16
> **BananaPeal said:**
> I was using the command line to automatically mount the drive on startup by running the command out of "startup appliations". 

That's a creative approach - I would have thought it would work, but fwiw here's the "official" way.

Assuming you have already created your mountpoint /media/windows, open the system file /etc/fstab for editing with root privileges with:

```
gksudo gedit /etc/fstab
```Go to the end of the file and add the following line on a newline. It doesn't matter if there is a blank line between the end and your new line.

```
/dev/sdb2   /media/windows    ntfs    defaults    0 0
```That will cause sdb2 to mounted read-write on bootup with an icon on your desktop, but to mount it once you've edited fstab, do:

```
sudo mount -a
```Don't let anyone tell you that you need any options apart from "defaults" - trust me. I've used "defaults" by itself for mounting ntfs partitions in every release of Ubuntu since Hardy on more than one machine and I've always had read-write capability as an ordinary user and with no problems. (In fact the extra options put in the fstab line for ntfs partitions by the Ubuntu installer does cause problems.)

If you still can't read-write the filesystem with this fstab line, then the problem is in the filesystem and you do need to run a chkdsk before you can rescue your files.

---

### Post by BananaPeal on 2010-03-16
Guys... I think I really messed it up now.

My plan was to go into the win7 installer and just do a clean setup. When I selected the drive (win thinks it's a primary partition) to install, it told me something along the lines: setup can't make the file system, look at the logfile (no idea where this exists...).

I thought, gee, if I delete the partition using the installer, it'll just start over and write everything from scratch... like I want. So I did. The error persisted and when I finally tried chkdsk it said there are problems that chkdsk can't fix ... now here's the command I ran:

hd0 is ubuntu 9.1
hd1 is messed up windows

X:\> chkdsk d: /f

so i imagine this meant fix hd1.

Anyways. Gparted says it's unallocated space. Win installer should have no problems right? 

Does anyone know what might be causing the installer error? It worked when the drive was brand new! Unallocated space means fresh clean drive right... ?

---

### Post by srs5694 on 2010-03-16
I could be wrong, but it sounds as if the partition has been deleted. The testdisk program in Linux may be able to recover the partition, but it will still have whatever corruption is causing problems. Still, I recommend you try this. You may then be able to mount the drive and retrieve your important files from it. If you were only planning to install Windows to recover those files, you can then reformat the partition for Linux or delete it and resize your existing Linux partition. If you still want Windows, then I'd use the Linux mkfs.ntfs program to create a new NTFS filesystem on the partition and re-install to the fresh partition.

---

### Post by coffeecat on 2010-03-16
> **BananaPeal said:**
> Anyways. Gparted says it's unallocated space. Win installer should have no problems right? 

Does anyone know what might be causing the installer error? It worked when the drive was brand new! Unallocated space means fresh clean drive right... ?

Not quite. There is also the partition table to consider. That might have been corrupted as well, sufficient to bemuse the Windows installer. If you have written off any data that was on that disc, open Gparted and then Device > Create Partition Table and create an ms-dos partition table. That will recreate it. Then see what Windows 7 makes of the unallocated disc but with a nice new shiny partition table.

Rather than use mkfs.ntfs I personally would use Gparted, but it might be better to let Windows 7 make its own partitions (if it co-operates). W7 likes to have partition boundaries in odd places (there are always a few MB spare between partitions) and by default it creates a separate 100MB partition for some of the Windows boot code. It will happily install to a single NTFS partition that Gparted has created (I've done it with the RC) but it might be preferable to let Windows have its own way.

Last thought. Will Windows 7 install to a secondary drive? I'm sure earlier versions wouldn't.

---

### Post by BananaPeal on 2010-03-16
> I could be wrong, but it sounds as if the partition has been deleted.

srs: I deleted the partition with windows installer. Didn't make it squeaky clean like I hoped.

> Last thought. Will Windows 7 install to a secondary drive? I'm sure earlier versions wouldn't.

coffeecat: the windows installer lists:

hd0, the linux partition as 'system'
swap space as 'secondary'
hd1, the 'unallocated space' as 'primary'

or... do you mean primary that it has to be the first drive with the MBR on it?

I'll try using Gparted to rewrite the NTFS partition table after i get NTFSprogs. Or should I do FAT32 then have the installer do it "it's own way"? Gosh. why can't windows get along with other OSes? I think I'd like to stay with Ubuntu but the spotty .docx support is kinda inconvenient.

Thanks again for your inputs guys.

---

### Post by coffeecat on 2010-03-17
> **BananaPeal said:**
> coffeecat: the windows installer lists:

hd0, the linux partition as 'system'
swap space as 'secondary'
hd1, the 'unallocated space' as 'primary'

or... do you mean primary that it has to be the first drive with the MBR on it?

I'm not 100% sure. I've always put Windows on the first drive (master in the old ide days) because it's easier that way and Linux is quite happy to boot from secondary drives so long as grub stage 1 is installed to the mbr of sda. Also, to get Windows to boot from sdb with grub, you have to use grub 'map' commands which adds another layer of complexity I can do without.

What I meant was that I thought I read somewhere that earlier version of Windows simply wouldn't install to a secondary drive. The installer wasn't designed that way. That's understandable because Microsoft has no interest in making Windows compatible with multibooting systems, and why would you put windows on a secondary drive if it's the only OS? I really don't know if this is the same or different for Windows 7. It may be that the Windows 7 installer is detecting both drives because the W7 partitioner is more sophisticated that the XP one (say) and that it's giving you the chance to set up complex partitioning schemes for Windows with E:, F: and so on (in Windows parlance) drives.

It's possible. I was just offering that as a thought. It might explain some of the difficulty of installing W7 to the secondary drive.

By the way: I'm using the words primary and secondary to mean sda = primary drive; secondary drive = sdb, sdc and so on. The 'primary' and 'secondary' that the Windows installer is reporting probably refers to something else. Also, the presence of a Linux filesystem and a Linux swap partition on sda might be confusing the hell out of it. It will detect them as valid partitions, but won't be able to make sense of the filesystem type.

---

### Post by BananaPeal on 2010-03-17
Okay. I'm gonna see how long I can go without it. And I'll relegate windows to the secondary drive just because this has been incredibly frustrating at times, and for no other reason than my own button pushing and M$'s crappy bootloader and fix applications. Ubuntu and Gparted were there for me when the drive died... windows7 couldn't figure out how to install itself...

My very last question: can you recommend an imaging program I can use to move my Ubuntu onto the replacement drive? It's bigger and faster than this one, which will soon house win7. And I'd like to not setup ubuntu and programs for a 3rd time...

Thanks again for your support. I'm very grateful to the community for helping me to get going.

---

