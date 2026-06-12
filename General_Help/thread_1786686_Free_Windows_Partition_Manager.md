---
title: "Free Windows Partition Manager"
date: 2011-06-20
forum: General Help
---

### Post by Supergoo on 2011-06-20
I sometimes run across people who want to install Ubuntu next to their Windows OS. There is a utility that can do that when you are installing from a Ubuntu CD, but some people might want to set it up before installing or on the other hand want to delete a partition that once was a Ubuntu Install without having to do a clean install, and they want to reclaim that space for use. After looking around I have found a Free Program that works well,and might fit the need.

The Program is called EASEUS Partition Master Home
You can find more information about it at this link below...

[http://www.partition-tool.com](http://www.partition-tool.com)

I hope this will help somebody who is in need of this type of App. 

Supergoo

---

### Post by idoitprone on 2011-06-20
I think window built in program is suffice

---

### Post by srs5694 on 2011-06-20
> **idoitprone said:**
> I think window built in program is suffice

I *strongly* advice *against* using the standard Windows partitioning tool to create partitions for Linux! The problem is that it tends to (silently, or close to it) convert partitions from standard MBR primary partitions into "dynamic disk" (aka LDM) form. This is a Microsoft format that's conceptually similar to Linux LVM, but it's difficult or impossible to install Linux to a dynamic disk, much less manipulate them within Linux. I see posts here once or twice a week from people who've converted their disks into LDM form and need help getting them back into a standard form so they can install Linux.

The Windows tools tend to convert to LDM form whenever the number of partitions exceeds four. Most PCs sold today come with three or four partitions, meaning that creating just one or two more partitions will kick you over the limit and create this problem.

FWIW, the EASEUS tool that Supergoo recommends is one of two programs I've heard of that's supposed to be able to undo the LDM conversion. I've never used the program myself, though, so I can't say how good it is.

If you want to get rid of a Linux installation, then I expect the standard Windows tools would do the job, but I've never tried using them for that. One caveat is that many Linux installations, including the standard method of installing Ubuntu, leave the computer dependent upon a Linux partition for booting, since GRUB is in the MBR. Thus, deleting the Linux partition will leave the computer unbootable. This problem is easily overcome by installing a new standard MBR. The Windows installation/recovery disc should be able to do this, using the [FIXMBR](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true) command. There are also various other ways to do this. IIRC, the [SYSLINUX](http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project) package includes a replacement MBR boot loader that should be compatible with a Windows-only installation.

---

### Post by idoitprone on 2011-06-20
Wait srs5694, you actually use a windows tool to prepare fully for ubuntu install. I am just saying he windows tool to unallocate space for ubuntu and let gparted or the installer do the rest.

---

### Post by CharlesA on 2011-06-20
> **idoitprone said:**
> Wait srs5694, you actually use a windows tool to prepare fully for ubuntu install. I am just saying he windows tool to unallocate space for ubuntu and let gparted or the installer do the rest.
I do the same thing. With Vista/7, resizing isn't as painful as it used to be.

---

### Post by wildmanne39 on 2011-06-20
Hi, most of the people that work with partitions and boot problems on here say that you should resize your windows partitions with windows, of course that does not work with xp or lower but for vista and windows 7 it does.

---

### Post by srs5694 on 2011-06-20
> **idoitprone said:**
> Wait srs5694, you actually use a windows tool to prepare fully for ubuntu install. I am just saying he windows tool to unallocate space for ubuntu and let gparted or the installer do the rest.

There's some serious miscommunication going on here. My precis of the thread so far:


[list]
[*]Supergoo advised using the Windows EASEUS program for two purposes: To prepare for a Linux installation (a bit unclear, but I took that to mean create Linux partitions) or to delete an existing Linux installation.
[*]You said "I think window built in program is suffice;" I took "suffice" to mean "sufficient," and that *you* were advocating using the standard Windows tools for preparing Linux partitions.
[*]I replied that the standard Windows tools should *not* be used to prepare Linux partitions, for the reasons I described, but that they might be OK for *deleting* Linux partitions.
[*]CharlesA and wildmanne39 have both chimed in that the Windows tools are useful for shrinking Windows partitions before installing Linux. I agree with this, but with the important caveat that those tools *not* be used to create new partitions.
[/list]


FWIW, my understanding is that the problem with the Linux tools for resizing Windows partitions is that if the start of the partition shifts, Windows becomes unbootable; and tools like GParted will sometimes shift the start of a partition without telling you. The Windows partition resizer makes the necessary adjustments so that such changes aren't a problem. This problem is becoming less of an issue for a couple of reasons:


[list]
[*]Recent versions of GParted now default to 1 MiB alignment, which is what Windows Vista and Windows 7 both use. Thus, with current software and recent versions of Windows, GParted *shouldn't* shift the start point of the Windows partition. This isn't guaranteed, though.
[*]On computers that boot through UEFI rather than using the old BIOS methods, Windows is much less picky. I've tested this: I did a UEFI Windows installation and then used GParted to move the Windows boot partition to an entirely different part of the disk (no overlap with the old location at all). It continued to boot just fine. UEFI-based systems are still rare, but many of the latest computers and motherboards have UEFI support, so this type of setup will become much more common in the next couple of years.
[/list]

---

### Post by CharlesA on 2011-06-20
> **srs5694 said:**
> 
[list]

[*]CharlesA and wildmanne39 have both chimed in that the Windows tools are useful for shrinking Windows partitions before installing Linux. I agree with this, but with the important caveat that those tools *not* be used to create new partitions.
[/list]


Yep. I'd use either gparted or the installer to create the new partitions for *nix to live on. You could also resize the windows partition that way, but I've usually do it using Windows tools - even tho I haven't had problems with either way.

---

