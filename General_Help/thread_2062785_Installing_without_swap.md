---
title: "Installing without swap"
date: 2012-09-25
forum: General Help
---

### Post by Wiking on 2012-09-25
Hi, got a new machine, wanting to do a triple boot.

Since the new rig has 16GB of RAM, and since I rarely logout or use hibernation I'm just going to skip the /swap partition.

So could I just make the /boot, /, and /home partitions and be good?

I've read here of other people setting their swap to zero, don't know exactly what that means, but is it necessary to make a swap however small?

thinking: 

/boot
/
/home

would be fine

---

### Post by Bashing-om on 2012-09-25
Wiking;

  With that amount of ram, I can see no problem installing with no swap under the given provisio.
 One might consider to leave a bit of space unallocated for future expansion or changes. In the event that a swap partition is desirable at some time...be an easy matter to make the changes.
 On that note I find a separate "data" partition is nice to have.

 There are pros and cons to separate /boot and /home partitions. Some advise there is little gain and some performance loss ... I personally have my system set up segregated 
and like the feeling of control this permits. I think it is a matter of personal preference.

[INDENT]imho ==> BDQ

[/INDENT]

---

### Post by ajgreeny on 2012-09-25
As Bashing-om says, forget about a separate /boot partition; it is only really needed on a server install and seldom any help on a desktop machine.  In fact it can make system administration more difficult.

Personally, I think a separate /home partition is definitely worthwhile.  You will still need to make backups of /home just in case, but when you need to update the OS or re-install, a separate /home is a huge help.  A separate /data partition can also be very useful, and if put on a ntfs partition can be used for all OSs, both Linux and windows (not sure about mac) without problems.

However, as long as you keep good backups frequently enough it is perfectly feasible to run a successful Linux OS with just a root partition, and with 16GB ram, not even swap is essential.

---

### Post by Moose on 2012-09-25
Lol im running fedora 16 on my laptop with no swap. And i only have 2GB of RAM. The installation process is the same as Ubuntu. Format your whole hardrive. Delete all partition. Convert Unused space into ext4. Make the mount point /. And your done. :D

---

### Post by Wiking on 2012-09-25
> **ajgreeny said:**
> As Bashing-om says, forget about a separate /boot partition; it is only really needed on a server install and seldom any help on a desktop machine.  In fact it can make system administration more difficult.



I just do it like that because I want to have 2 linux distros alongside w7. That way I can load grub onto the /boot.

---

### Post by HiImTye on 2012-09-25
just remember that without a swap partition, you may not be able to figure out why some system errors occur. it's generally advisable to keep at least *some* swap space, just in case. a swap partition just makes it easier than having a separate swap *file* for each partition. even Windows keeps a swap (page) file, just in case.

of course, if you already know all this, by all means go ahead and run without it. it is your system, after all :)

---

