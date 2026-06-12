---
title: "What are mount points for?"
date: 2009-10-21
forum: General Help
---

### Post by szaemon on 2009-10-21
Where can I find information on the different mount point options available at installation? I understand the value of partitioning root from home, but I don't get the practical value of the other mount points. I want to understand why they are there and in what situation I would find them useful.
Please point me toward the proper reading material.
Thanks.

---

### Post by Tony Flury on 2009-10-21
Ok - the main uses of mount points from what i can see : 

1) To share common data between multiple versions of the OS - you do this on /home - but you could do this with /boot as well (so you get a single unambiguous grub menu) - /swap also tends to be shared between versions.

2) To Limit the amunt of space that a particular part of the file systems uses - a good way would be to partition out /tmp and/or /var if the applications produced a lot of temp files or log files.

3) To allow you to share certain parts of the file system between different machines - a common set up would be to have /home mounted from a remote server - so each PC acts as smart terminal - it runs the OS - but you can in theory log in from any PC on the network and get to all your files.

---

### Post by nothingspecial on 2009-10-21
As I understand it, the reason for having /var on a seperate partition ,is that if your computer devolops a serious problem the error logs in there can quickly fill up your hard disk.

For the same reason some programs write data to temporary files in /tmp, if you're running the large hadron collider or something like that gigabytes of data could be written to /tmp in a short space of time.

If you have them on a seperate partitions, this wont effect your root partition.

This isn`t really necessary om a home pc

---

### Post by P4man on 2009-10-21
> **szaemon said:**
> Where can I find information on the different mount point options available at installation? I understand the value of partitioning root from home, but I don't get the practical value of the other mount points. I want to understand why they are there and in what situation I would find them useful.
Please point me toward the proper reading material.
Thanks.

You probably never need it. But in specialized cases it can be good to have certain mount point on specific drives, like putting /swap or /tmp on a dedicated hard drive or nas or san or ssd well suited or large enough for the purpose, or to make backup procedures easier or whatever. For a "home user" there is not much point besides separating / and /home.

---

### Post by Tony Flury on 2009-10-21
> **P4man said:**
> You probably never need it. But in specialized cases it can be good to have certain mount point on specific drives, like putting /swap or /tmp on a dedicated hard drive or nas or san or ssd well suited or large enough for the purpose, or to make backup procedures easier or whatever. For a "home user" there is not much point besides separating / and /home.

I disagree - i would strongly recommend that the default advice should be to seperate / and /home, as it provides a simple upgrade path without having to fiddle about pre upgrade copying all of your key files - you just insert the CD - tell it where / and /home are and bingo - a few minutes later and upgraded system with ALL of your personal files intact - not negating the need for backups just in case. In fact I am not sure why the Ubuntu installer can't detect the existance of existing / and /home - and offer a tailored upgrade.

---

### Post by P4man on 2009-10-21
> **Tony Flury said:**
> I disagree - i would strongly recommend that the default advice should be to seperate / and /home,

reread my statement :) I said **besides** separating / and /home (wich the OP already stated he understands). So I agree with you, Its just that having dedicated mountpoints for /tmp or /process is not likely useful for a home user. Separating /home however is a very good idea for the reasons you list.

---

### Post by Tony Flury on 2009-10-21
OOps - sorry 

I was meant to be working at the same time - but replying to an IM from my manager and replying to a post here at the same time don't mix.

Sorry again.

---

### Post by mcduck on 2009-10-21
One point is that different directories serve different kind of purposes, and might be under very different types of load. In server environments (and other non-home computing environments) it might make a lot sense to select different filesystems (and possibly RAID setups) for different directories to get the best performance & reliability.

This feature can be very useful for home users as well, at least in some cases. For example SSD drives have small capacity and limited write cycles, but otherwise perform great as system drives. So if you had a computer with a SSD and a normal hard drive, you could place most of the system on SSD, while keeping those directories that have heavy write access (like /tmp and /var), as well as those requiring lost of space (like /home) on the normal hard drive.

Still, the basic idea is that any directory can be mounted on any separate physical drive, and on the other hand any drive can be mounted anywhere you want in the directory hierarchy. So the installer must also allow configuring this, it wold be quite annoying to have to do it manually *after* the install.

(edit: By the way, I *never* use a specific /home partition. I actually *want* to clean all the setting files in my home directory during release upgrades. Instead I have a separate /storage partition, with directories for all different types of files symlinked into my home. This way I can keep all my files and backup all the setting files I know I want to keep through upgrades while still getting rid of all the extra stuff that's accumulated into my home directory over time.)

---

### Post by szaemon on 2009-10-22
Hey thanks for all the feedback folks. /tmp and /var I understand now.
How much space do you recommend the average user should set aside for them? And what happens if the space does fill up? Would the system crash?

> **Tony Flury said:**
> 
1) To share common data between multiple versions of the OS - you do this on /home - but you could do this with /boot as well (so you get a single unambiguous grub menu) - /swap also tends to be shared between versions.

Flurry, I don't quite get your meaning here in regards to /boot , probably because I don't really know how grub functions. What do you mean by a single unanimous grub menu? As I know the grub menu, it pops up with a list of operating systems to choose from...and I choose. What would be different?

---

### Post by P4man on 2009-10-22
> **szaemon said:**
> Hey thanks for all the feedback folks. /tmp and /var I understand now.
How much space do you recommend the average user should set aside for them? 

The average user wouldnt split them, the non average user would probably know :). But I guess a few gigabytes (say 10 to be safe) would do in most cases.

> 
And what happens if the space does fill up? Would the system crash?

Possibly.
> 
Flurry, I don't quite get your meaning here in regards to /boot , probably because I don't really know how grub functions. What do you mean by a single unanimous grub menu? As I know the grub menu, it pops up with a list of operating systems to choose from...and I choose. What would be different?

Grub typically resides on the same partition as your ubuntu in /boot/grub. But if you have several (linux) OSs, it can be a good idea to give grub its own partition so for instance wiping one OS partition doesnt kill grub. Its also necessary to put grub on its own partition if you install ubuntu on a (software) raid. This changes nothing to how it appears though.

---

### Post by mcduck on 2009-10-22
> **szaemon said:**
> Hey thanks for all the feedback folks. /tmp and /var I understand now.
How much space do you recommend the average user should set aside for them? And what happens if the space does fill up? Would the system crash?



Flurry, I don't quite get your meaning here in regards to /boot , probably because I don't really know how grub functions. What do you mean by a single unanimous grub menu? As I know the grub menu, it pops up with a list of operating systems to choose from...and I choose. What would be different?

Unless you actually have a specific reason to do so, you shouldn't make any extra partitions. You'd just end wasting your disk space (one partition running out of space while another has way too much) for no benefit at all.

For any normal home use you should either only have a root and a swap partition, or root, swap and a separate home/storage partition.

---

### Post by louieb on 2009-10-22
> **mcduck said:**
> ... For any normal home use you should either only have a root and a swap partition, or root, swap and **a separate home/storage partition.**

+1 - the longer I use computers the more I realize the importance of keeping data on a different partition from the OS. For me its 3 partitions: 1 for the OS, 1 for swap. and 1 for data storage.

---

### Post by QLee on 2009-10-22
[QUOTE=szaemon]Where can I find information on the different mount point options available at installation? I understand the value of partitioning root from home, but I don't get the practical value of the other mount points. I want to understand why they are there and in what situation I would find them useful.[/QUOTE]

When I read this it seemed you might be asking about the various directories (folders) in "/" but calling them mount points.  But I may have misinterpreted what you wrote. Of course, one can add any "mount point" they require by creating a location for it.


This document might be helpful to learn something about Linux file structure:
Linux Filesystem Hierarchy
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

It was written a while ago but these things don't change rapidly. It is not Ubuntu specific, still would probably get you started with understanding or give you specific questions to ask.

The rest of the thread posts have plenty of opinions for some various ways of provisioning a system.

---

### Post by szaemon on 2009-11-03
Thanks again for all the feedback. I think I see what I want to do now. The basic 3 I've already been using:root,swap and home. Boot makes sense to me too now, since I'm often running a test OS in prep for an upcoming new release, as well as UE for games.
I think I'm all set now.
Thanks again folks!
szaemon

---

### Post by ratcheer on 2009-11-03
In simple language, the purpose of mount points is that in UNIX-type systems, everything must be a subdirectory of / (root). However, for performance and manageability reasons, you do not want everything to actually be part of the root filesystem. So, you mount other filesystems and they become part of the root hierarchy without actually being in root.

Tim

---

### Post by wildweathel on 2009-11-03
Further reading?   LVM.  If you're doing anything more complicated than Ubuntu-swap, Ubuntu-root, Windows 3-partition-1-disk scheme, you want to know about [Logical Volume Management]("http://www.google.com/search?q=linux+lvm&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a").  

I'm considering re-installing.  If so, it would look like this:

Swap (2GB)
/boot (1GB)
LVM:
 - / (5 GB)
 - /home (40 GB)
 - downloaded-media (120 GB)
 - XP (20 GB)
 - ubuntu+1 swap (2 GB)
 - ubuntu+1 / (5 GB)
- squeeze / (5 GB)

Which totals 190 GB on a 300 GB drive.  The remainder gives me room for snapshots or growth.  Read about snapshots.  Totally blow your mind.  

LVM snapshots + debootstrap + apt-cacher + Virtualbox/KVM/Xen = 5-minute instant test computer.

---

### Post by szaemon on 2009-11-10
WoW! That's a lot to go through. For now at least, I think I'll just stick to the basic 3 plus 1 for a Beta Ubuntu.
Thanks.

---

