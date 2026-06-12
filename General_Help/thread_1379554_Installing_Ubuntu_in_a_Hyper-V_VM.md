---
title: "Installing Ubuntu in a Hyper-V VM"
date: 2010-01-12
forum: General Help
---

### Post by poecke on 2010-01-12
First of all, I'm not sure where to put this, since I'm running into multiple problems.

Here's my story: I got tired of my old debian installation in my Hyper-V VM, so I decided to try Ubuntu on it. Mainly because I hoped Ubuntu would be a bit more user friendly.

I used all the normal settings(from my Debian VM) and started with Ubuntu, and of course, I ran into huge problems.

First of all I was surprised to see that Ubuntu only found 137 GB of my 1.5 TB virtual hard disk, which of course, is rather problematic.
I found out that this has something to do with a 28-bit LBA, meaning that 137GB would be the limit for the harddrive. I searched for hours for a solution, nothing works. The problem isn't my hostmachine(windows server 2008 ), because it finds my 2TB raid array without any problems.

Then I tried method #2; making 2 virtual HD's, a small one for my OS, and a big one for the data. The idea was to mount the second one as an SCSI controller. It still seems like a good idea, except that the linux integration for Hyper-V is really a joke, and without proper integration the controller can't be found. I tried consulting numerous guides, but they all refer to older versions of Ubuntu, and I prefer to be up-to-date.

After two days of trying random googled stuff, I feel like crying, since this is a problem which simply shouldn't occur after 2003(28-bit LBA *cry*). 


I hope someone can give me some good advice, otherwise I'll go back to Debian.(which would be ridiculous, as Ubuntu is based on that)

Thanks in advance.

Edit: In a last ditch effort I'm going to try this guide, [http://blog.allanglesit.com/Blog/tabid/66/EntryId/43/Hyper-V-Guests-Compile-Linux-2-6-32-on-Ubuntu.aspx](http://blog.allanglesit.com/Blog/tabid/66/EntryId/43/Hyper-V-Guests-Compile-Linux-2-6-32-on-Ubuntu.aspx) *cross fingers*

---

### Post by sztupy on 2010-02-23
Hi!

I made a component that has the Microsoft's installer ( [http://www.microsoft.com/downloads/details.aspx?FamilyID=c299d675-bb9f-41cf-b5eb-74d0595ccc5c&displaylang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=c299d675-bb9f-41cf-b5eb-74d0595ccc5c&displaylang=en) ) but with the latest Hyper-V code, that works with the 2.6.31 kernel ubuntu (server) 9.10 has. You only need the kernel headers and gcc, but don't need to recompile the whole kernel.

Installation:
1. DL: [http://sztupy.hu/static/hyper-v-ic-kernel-2.6.31.zip](http://sztupy.hu/static/hyper-v-ic-kernel-2.6.31.zip)
2. extract
3. sudo ./setup.pl drivers
4. If succesful add vmbus, netvsc, blkvsc and storvsc to /etc/modules

---

### Post by babarehner on 2010-11-17
I've been working on a 10.04 install into Hyper-V. The link is at [http://www.babarehner.com/ewrench1011/VirtualMachines/index.html](http://www.babarehner.com/ewrench1011/VirtualMachines/index.html)

---

