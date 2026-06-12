---
title: "Confused - questions in the way [kernel compile and volume management]"
date: 2011-08-27
forum: General Help
---

### Post by ClientAlive on 2011-08-27
There's this project that I've been stuck on for way too long now. I've made a lot of progress learning wise but have had some trouble finding answers to some of my questions. I continue to research, and am learning a lot about the general stuff (which I think I need to know too) and even steps on certain procedures; but, for some reason, there are still these few questions I'm stuck on.

The idea is to compile a kernel for Xen, compile Xen and get to using it (in a nutshell. I also want to address the issue of volume management in that system too though. I have four questions. One is kinda stand alone, the other is kinda stand alone, and the third is more connected to those first two, and the fourth is completely on it's own/ not connected. I'll do my best to state them that way. Maybe someone can help clear the confusion for me?

1) That computer has no formatting on any of it's disks (there are 3 of them - slightly different capacities). Does there have to be some kind of formatting on the disk before the kernel can be compiled on it? If so, do I need to take the file system type into consideration for other things/ reasons that may come up down the road (volume management for instance)?

2) As for volume managemnet:

On the one hand, I have 3 IDE disks in the machine; and, while close to one another in size, they are not identical in size. On the other hand I'm a bit enamored by RAID (RAID 5 is the one that seems to be rising above the other's at this time). The smallest disk is 75.9 GB but lets just call it 76 for simplicity. The largest disk is 100 GB.

From what I've read about standard RAID, it will use the smallest disk as the common denominator. I don't like that idea at all (a roughly 24 GB waste). I got to wondering if there isn't some way around this problem that would allow me to not only use RAID but make full use of the disk space, on all disks, as well.

What I came across is something called MDADM. MDADM claims it can RAID across partitions but I'm not sure that means what I hope it does. This leads me to my #2 question:

_Can MDADM RAID across partitions when there are other partions on the disk?_ Let me clarify. I don't mean that RAID would be contained to one disk, I mean that there would be more than one RAID array across all three disks and/ or partions on disks that don't have RAID on them but RAID is on that disk (just across a different partition). This would require management between one partition and another regarding read/ write tasks. Priorities would have to be in place or a guy might even do some damage (I suppose).

So let me give a simple, arbitrary example to illustrate:

Lets suppose a person had two disks in their machine. One disk (sda) is 50 GB and the other (sdb) is 55 GB. He wants to partition the devices and use the partitions thus:

sda1 50 GB (for RAID aray)
sdb1 50 GB (for RAID aray)
sdb2 5 GB (swap)

He thinks that he could either use MDADM or this other idea he has; to RAID across the two 50 GB partitions and still not lose that other 5 GB of space on sdb. The problem is there would have to be some way to manage what partition on sdb gets the attention of the read/ write head and when, and it would have to manage it in such a way that it doesn't bring the entire system to a halt in doing so.

And so he wonders. Does MDADM just work that way out of the box? Is he hoping for too much or can MDADM really do that?

If he finds out MDADM can't do that he has a couple ideas he wonders might work. The ideas are not well formulated but he thinks it may involve 'niceness' and/ or asynchronous writing with the RAIDed parts of the disks. Is he on the right track?

Also, and I probably didn't do a very good job of describing, and it is a little more complicated than the example I used, but here:

[http://ubuntuforums.org/showthread.php?t=1830461](http://ubuntuforums.org/showthread.php?t=1830461)  Edit: See post #3

is the link to a thread where I show exactly my desires for those three disks using actual sizes - ideas all mapped out.

3) I read that MDADM needs to have RAID support built into the kernel and also discovered that it seems to be something that is installed into an already functional operating system. MDADM also, by nature, deals with the topic/ issue of file systems (as in ext3, ext4, nfs, etc - if I'm not mistaken???). So then, if it is the case that I need to have a file system formatted on my disk before I can compile my kernel onto it, yet MDADM has, to some extent, to do with formatting file systems - what then do I expect this whole thing to play out like?

??

a) format file system onto disk
b) compile kernel/ Xen/ etc - to get a working system (but by that time all your disks are part of the system/ of a working system and the system is on the disk you would later, what?, start making these dramatic file system changes to??)
c) install and use MDADM (and what, be formatting file systems and making all kinds of changes to disks which already have software data on them?)

??

I don't get it.

4) Considering the state of my hardware (there is no operating system installed on it/ it's just bare) - it would seem to me the most desirable way to do my compile is through a live cd or usb and compile what I want right onto the disk the first time. Can that even be done? If it can, what are the most basic tasks I will be using in order to do it that way? Can you name off the biggest, most general things I will be doing to accomplish it that way? Would one of them involve something called 'chroot'? 'chroot' to what? (If it's live it's different and so are the hardware labels aren't they??)


All in all I suppose 'one of' the big blanks for me that I'm trying to get filled in is the whole idea of setting up my environment for compile. I have seen one source (the Gentoo manual) that addresses partitioning the disk as part of that setup but I don't see that it addresses my question about needing a working o/s or not to do a compile and whether it can be live if you do have to have that. It lists programs (a compiler for instance) that you need to have to do a compile but install those programs to what/ where? To a working o/s? And it has to be physically installed on the disk you'll end up not wanting it on when you're all done?


If there's any part of this you can help me with I would sure appreciate it. These things have really gotten me stuck. I'm the kind of guy that needs (I mean neeeds) some kind of a track to go on or I don't understand where I'm supposed to be heading. These kind of questions bring me to a standstill until I get them cleared and can, ultimately, see a clear path not from a to b but from a to z.

Thanks in advance for your help and for taking the time to read this.


Jake
:)

---

### Post by searchfgold6789 on 2011-08-27
[LIST=1]
[*]Yes; no. Although you should probably use something standard like ext4.
[*]I don't understand RAID ):
[*]
[*]Yes. You will need to install an operating system onto your computer and do all of the compiling and installing there, just like everyone else (:>
[/LIST]
Beyond that, I wish you luck with your project, and I hope someone more experienced than me will take sympathy!

---

### Post by ClientAlive on 2011-08-28
> **searchfgold6789 said:**
> [LIST=1]
[*]Yes; no. Although you should probably use something standard like ext4.
[*]I don't understand RAID ):
[*]
[*]Yes. You will need to install an operating system onto your computer and do all of the compiling and installing there, just like everyone else (:>
[/LIST]
Beyond that, I wish you luck with your project, and I hope someone more experienced than me will take sympathy!


Thanks searchfgold6789. Love your signature, by the way.

---

### Post by sbraz on 2011-08-28
yes you can have partitions outside the lvm.
the /boot partition is normally a 100-300MB ext2, then the rest is lvm.

if you make a raid via software like using LVM you can allocate space however you want as it works with logical volumes. general RAID rules apply anyway:
if you stripe/mirror some partitions the smaller volume determines the maximum size.

your kernel must be configured for LVM enabling the required modules under "Device Drivers  ---> [*] Multiple devices driver support (RAID and LVM)".

notice that with lvm, you use your CPU to route your data across 
the array. hardware raid doesn't have this disadvantage as most of the processing is done by it's dedicated chip.
also, if you make a raid 5 on a 3 disk two-channel PATA setup there will be a lot of transfer concurrency on one of the channels so depending on the amount of I/O your performance might be slower than expected.


i prefer the classic hardware raid but i understand that LVM offers some good degree of flexibility, like creating a raid 5 volume using a single drive and such. :)

---

### Post by ClientAlive on 2011-08-28
> **sbraz said:**
> yes you can have partitions outside the lvm.
the /boot partition is normally a 100-300MB ext2, then the rest is lvm.

if you make a raid via software like using LVM you can allocate space however you want as it works with logical volumes. general RAID rules apply anyway:
if you stripe/mirror some partitions the smaller volume determines the maximum size.

your kernel must be configured for LVM enabling the required modules under "Device Drivers  ---> [*] Multiple devices driver support (RAID and LVM)".

notice that with lvm, you use your CPU to route your data across 
the array. hardware raid doesn't have this disadvantage as most of the processing is done by it's dedicated chip.
also, if you make a raid 5 on a 3 disk two-channel PATA setup there will be a lot of transfer concurrency on one of the channels so depending on the amount of I/O your performance might be slower than expected.


i prefer the classic hardware raid but i understand that LVM offers some good degree of flexibility, like creating a raid 5 volume using a single drive and such. :)


Awesome!

Well, I cooked up a much simpler scheme that I think will even suit my purposes better. I see a lot of general information on the internet about using mdadm but not as sure what to do when it comes to my specific intentions. I have an idea what I need to do and think I'm going to just start fiddling with it pretty soon here to see.

I'm hoping I can find a fast effective way to test my setup at this stage before proceeding to compile a bunch of stuff. I'm really hoping to limit wasted effort and I know if I have to do things over several times to get it right then the more you have to do over the more you have to do total (it adds up).

One of the things I know I need to look into is the partitioning scheme to use for the system I'm trying to build. I think that once I have those two big pieces (lvm and partitioning scheme) mapped out I'll be ready to start my fiddling :) I'm coming to the conclusion that the way this will have to play out is primary partitions in order to do my lvm scheme and logical partitions within that for the actual system. If that's the case, I just hope there's no problem using logical volumes for a system.

Well, back to google for a bit I guess.

Thanks for your help.

---

