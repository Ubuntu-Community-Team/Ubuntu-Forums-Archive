---
title: "Restored partition table - cant find swap disc? (red hat)"
date: 2011-10-14
forum: General Help
---

### Post by keneid on 2011-10-14
Hello! 

I know this is a ubuntu forum, but I hope i will get some help with my red hat, same as centos. 

I would expand a disk in vmware (machine was alive) and the virtual machine did not start up after the reboot. Started GParted and saw that the entire disk was unallocated.
Got a pain in the heart !

Thanks to the person who wrote this thread:
[http://ubuntuforums.org/showthread.php?t=370121](http://ubuntuforums.org/showthread.php?t=370121)

I found two partitions on sda. Sda1 = boot disk and 125mb main hard disk of 112GB. Indescribably ecstatic!

**MY PROBLEM**
Virtual machine will not start up again.

What do I do next? I can not find the swap partition. Is the "bootsystem" the problem? Is there something I can fix by using a LiveCD (like fix boot)?  I am running red hat.

EDIT
/dev/sda1/ boot1    <<-should i rename to only boot ?
/dev/sda2/ /1       <<-should i rename to only / ?
/dev/sda3 swap <<--- cant find - missing!


Thank you!!

---

