---
title: "Resize original windows partition"
date: 2011-06-16
forum: General Help
---

### Post by Chris Psycho on 2011-06-16
Hey guys. I'm trying to increase the size of my windows partition. I booted with the ubuntu live cd, and I made the ubuntu partition smaller, but for some reason even though there is free 'unallocated' space and I try to resize the windows partition it says 0 mb free?

LoL this is going to sound a bit dorky but, in the Gparted diagram, it seems the windows partition is in a separate 'box'. And the 'ubuntu/swap/unallocated' are all 'sub?' partitions of a separate 'box'.

Any ideas? :) much appreciated

---

### Post by seawolf167 on 2011-06-16
I ***highly ***recommend resizing the Windows partition with the built in partition editor through Windows itself (right click "My Computer", select "Manage", go to "Disk Management", then resize the partition). You'll have to have the unallocated space "next to" the existing NTFS partition to expand the partition into it. Windows shouldn't have any problems doing this.

---

### Post by coffeecat on 2011-06-16
> **Chris Psycho said:**
> 
Any ideas? :) much appreciated

Yes. Post a screenshot of the Gparted window so that we can see exactly what is going on. :wink:

By the way, once we've seen what the problem is, and resolved it, it will be much safer to resize the Windows partition with Windows' own Disk Management. Don't try that yet, though. Let's see the Gparted window first because Gparted is much better at showing what's on the hard drive.

---

### Post by Topsiho on 2011-06-16
I agree with seawolf167, that you should do changing Windows partitions within Windows itself. If you do it using another application, Windows will detect something is changed next boot, and refuse to boot.

Topsiho

---

### Post by Chris Psycho on 2011-06-18
I tried Easeus Partition Manager, I couldnt resize my 'ntfs' partition so i made a new one from the unallocated partition(?). (Its labelled bob)

Its 40gn for windows, 20gb bob, and then I have a linux mint installation and ubuntu...

By the way did I mention I cant boot?........
I think it said:
File system error
grub rescure>


.................... Much appreciated for any help :)

---

### Post by coffeecat on 2011-06-18
The different "boxes" that you mention in your first post are because most of your partitions are in an extended partition. Your first partition, /dev/sda, is a primary partition. That, I guess, is your Windows partition. You are allowed a maximum of 4 primary partitions. In order to exceed this maximum, one primary partition may be an extended partition. Your extended partition is /dev/sda2. An extended partition is merely a special type of extended partition whose sole purpose is to act as a container for a number of logical partitions. Your logical partitions are those numbered sda5, 6, 7, 8 and 9. One of the "boxes" was sda2, containing all the logicals. Primary (or extended) partitions are always numbered between 1 and 4. Logical partitions are numbered 5 and upwards.

My guess is that the free space you mentioned in your post #1 is what is now occupied by the "bob" partition, sda6. If this is so, there were two reasons why you could not enlarge your Windows partition into that space. It was taken by the extended partition and could only be used for a logical partition. A primary partition cannot extend into an extended partition. Also - the Windows partition and the free space were not contiguous, that is, adjacent. You cannot have a partition physically split up.

With regard to your booting problem. Boot up an Ubuntu live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script as described there. Post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] icon in the message toolbar for this.

---

### Post by Chris Psycho on 2011-06-24
Well I reinstalled grub and then could boot and access my 'bob' partition via... Haven't even tried booting into ubuntu...

Thanks everyone for your help  :)

---

