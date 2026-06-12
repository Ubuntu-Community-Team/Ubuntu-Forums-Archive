---
title: "Removing Ubuntu - Back to Windows"
date: 2010-08-03
forum: General Help
---

### Post by nall92 on 2010-08-03
Here's the deal, I use Ubuntu on both my laptop and my desktop - When I got this laptop (Windows 7) I created a Acer Windows recovery disc and then installed Ubuntu. I'm now giving this laptop away to a friend, however she would rather it had Windows. (that's all she knows!)

So I decided I'd try using the recovery disc I created, however I'm getting some sort of error when trying to recover it back to Windows 7, Windows won't install I'm guessing because Ubuntu is on the C drive.

Please if anyone knows how I can get Windows back onto C please let me know.

---

### Post by mendhak on 2010-08-03
Your Acer Recovery DVD should give you an option to format - do you have that, and if so, have you tried formatting the hard drive so that it goes back to factory settings? 

Also, post the error message.  The exact error message.

---

### Post by Dr_Willis on 2010-08-03
delete all the linux partitions with either a live cd and gparted, or fdisk, or in windows. then try the restore disks again. they may REQUIRE specific drive partitioning layout to work.  they 'should' repartition a totally empty (unpartioned) hard drive how they need to be.

---

### Post by QIII on 2010-08-03
Even if you attempt to reformat with your recovery disk, you may run into trouble if the Windows utilities barf when they run into ext4.

Use gparted to get a single, clean NTFS formatted drive.

---

### Post by nall92 on 2010-08-03
Here is the exact error I'm getting:
> Restore failed - Error Code=1005(The volume does not contain a recognized file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted.)About gparted, can someone give me basic instructions on how to to this? I'm guessing I'd need the livecd yeah?

---

### Post by Smart Viking on 2010-08-03
> **nall92 said:**
> Here is the exact error I'm getting:
About gparted, can someone give me basic instructions on how to to this? I'm guessing I'd need the livecd yeah?

Hey, boot into the machine with a live CD, open gparted and delete everything and make it one big NTFS partition, than windows should work. :)

---

### Post by cmcanulty on 2010-08-03
Yes you can't partition the boot partition except from the live disk.

---

### Post by nall92 on 2010-08-03
Attempting this now - will post back.

Thanks to everyone who has replied so far.

---

### Post by nall92 on 2010-08-03
This is working guys, thanks a lot! =D>

---

### Post by nall92 on 2010-08-03
Windows re-installed OK however when I turn on the laptop I know get this:

```
error: unknown filesystem
grub rescue >
```
Any idea how I can get Windows to boot?

---

