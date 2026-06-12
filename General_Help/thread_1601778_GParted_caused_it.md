---
title: "GParted caused it"
date: 2010-10-20
forum: General Help
---

### Post by wutuw on 2010-10-20
Hello everyone,

I'll try my best to describe what I did prior to my error.

I was getting ready to upgrade from Lucid to Maverick. I was backing up some of my vital documents but I didn't have access to an external storage device. So I shrunk an existing ntfs partition using Windows, and created an additional ext4 partition. Its size wasn't enough but I thought if I moved some of the files there (which were initially in the same partition with Lucid) and shrink the old partition to make room for the new one.

After copying the files, I tried to use the live CD and GParted to perform necessary operations. I left the computer after pushing apply but when I came back, I was greeted with an error message. Apparently, error occurred right before finishing the first task, which was shrinking of the old partition. So I know that most of the files are safe somewhere on the hard disk.

Here's the kick: I cannot, in any way, mount any of the partitions. I tried booting using the hard drive, using the live CD, the live CD of GParted. I even tried Windows out of desperation... Nothing.

I know it was too long, but I'd be really happy if anyone tried to help.

---

### Post by bruno9779 on 2010-10-20
Try to recover the partition with testdisk.

I usually log in with a live-cd or live-usb and install testdisk with apt-get, I don't think you can use it from your Ubuntu install.

---

### Post by wutuw on 2010-10-20
> **bruno9779 said:**
> Try to recover the partition with testdisk.

I usually log in with a live-cd or live-usb and install testdisk with apt-get, I don't think you can use it from your Ubuntu install.

Thanks for the reply.

testdisk gets stuck right after I select the harddrive. Something similar happens at GParted too. I think they try to get a response from the harddrive but just can't.

AFTER A WHILE

It did respond. I am trying to proceed further. I'll post the results.

---

### Post by wutuw on 2010-10-21
After trying a number of methods I'm still unable to reach the files.

On top of that, the hard disk is very slow. First I thought it was because the partition table was corrupted. But even after fixing the partition table, it is still slow and cannot be read by GParted.

Any ideas?

---

### Post by srs5694 on 2010-10-21
I recommend you check the SMART status. If the drive has developed one or more defects, that could explain all the problems you're seeing. I'm not saying that's certain or even highly probable, but it is possible, and it's worth checking.

You can check SMART status with any of several tools. I like GSmartControl, but the text-mode smartctl works, too, and I think Disk Utility in recent Ubuntus can check it, as well.

---

