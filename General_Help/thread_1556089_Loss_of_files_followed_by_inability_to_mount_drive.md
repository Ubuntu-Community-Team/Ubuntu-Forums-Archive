---
title: "Loss of files followed by inability to mount drive - help?"
date: 2010-08-18
forum: General Help
---

### Post by creativelies on 2010-08-18
Apologies in advance for the slightly long-winded explanation.

We've had a headless server running Ubuntu for a few weeks now and it's been fantastic - we've been able to access it from all of our computers and it's making life so much easier having one central box to put everything in.

Until yesterday, where we noticed that some directories on the 1TB HDD were empty that were previously full of files.  Restarted and the directories are gone, leaving only the root directories.  Restarted again and Ubuntu doesn't even recognise the disk.

We have Ubuntu installed on a 250GB HDD with the 1TB hard drive mounted on (as?) /srv and all of the data is on there.

Before Ubuntu stopped recognising the disk it would appear in Disk Utility saying that the file system was corrupted and that there was an issue with the superblock - I've found some ways of attempting to fix that but none are working now that Ubuntu isn't able to find the disk.

I've checked the physical connections and they all appear to be working fine.  I can hear/feel the hard disk spinning.

Some users haven't backed up the files they put on the server so I'd prefer to try anything non-destructive first and save their work.  I'm hoping that the HDD hasn't totally died... but now that Ubuntu can't see it I'm concerned that that might be the case.

Any thoughts?

If it helps:

Currently updated version of Ubuntu 10.?
System HDD is ext4
1TB problem HDD is ext3

---

### Post by earthpigg on 2010-08-18
is the hard drive recognized from a LiveCD?

is it regognized if removed from that system and placed in another?

---

### Post by silbak04 on 2010-08-19
If you can boot into the LiveCD, try chroot, mount everything and back up all the things you need on usb or whatever may be convenient for you. Here's a tutorial on chrooting:

[http://superuser.com/questions/111152](http://superuser.com/questions/111152)

---

### Post by creativelies on 2010-08-19
> **earthpigg said:**
> is the hard drive recognized from a LiveCD?

is it regognized if removed from that system and placed in another?

I have been booting from a LiveCD - it isn't recognised by that.

Oddly, it's now recognised when I boot into Ubuntu from the other HDD - there's now 4 remaining empty folders on it that I can see and that's all.

I still can't see it when booting from CD afterwards, though.  When I'm looking at it from the usual Ubuntu system it's at /dev/sdb1.

The HDD is recognised by my Mac when I stick it in there - it doesn't recognise the file system but it knows there's a hard drive there.

Does that make sense?

---

### Post by creativelies on 2010-08-19
> **silbak04 said:**
> If you can boot into the LiveCD, try chroot, mount everything and back up all the things you need on usb or whatever may be convenient for you. Here's a tutorial on chrooting:

[http://superuser.com/questions/111152](http://superuser.com/questions/111152)

I'll do some reading up on that and give it a shot - thanks.

---

