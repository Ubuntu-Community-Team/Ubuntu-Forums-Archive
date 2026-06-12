---
title: "ubuntu install on laptop alongside vista"
date: 2012-01-12
forum: General Help
---

### Post by shresthanator on 2012-01-12
He is trying to install ubuntu alongside vista on his laptop. Like he wants to have it dual-boot so that he can switch in between them. 

We are following this: 
[http://www.techspot.com/vb/topic172128.html](http://www.techspot.com/vb/topic172128.html) 

however we get to the step where we are supposed to have the option to "install ubuntu along-side vista". 

It does not give us that option. 

We have the option to "replace vista with ubuntu...." "other...." but not to automatically install vista alongside ubuntu. 

I have installed ubuntu alongside vista and windows7 but I don't think I ever encountered this before. We are just trying to avoid manually re-partitioning the hard-drive. He has 250 gig NTFS right now for his vista, and we don't want to do it manually.

---

### Post by CaptinGoogle on 2012-01-12
Is the Windows Vista partition taking up all of the hard drive space?

---

### Post by shresthanator on 2012-01-12
> **CaptinGoogle said:**
> Is the Windows Vista partition taking up all of the hard drive space?

yea he thinks it is, since that is the only thin on there right now

*it shows that there is a 238 Mb partition, but not sure why thats there, but the 250 gb is NTFS windows.

---

### Post by bindraj on 2012-01-12
Ubuntu can install with any of microsoft windows on seperate harddisk partition as well as on a seperate windows folder

---

### Post by CaptinGoogle on 2012-01-12
That small partition is where Windows keeps it's boot information. Your friend will have to re-install Windows Vista on a smaller partition. Then he will be able to install Ubuntu.

You could try the partition editor on the Ubuntu Boot drive, however, I would not recommend it.

---

### Post by topsites on 2012-01-12
It shouldn't be a problem because I installed dual-boot on my netbook and there is no way I could re-install Windows because all they gave me is a recover-partition and no cd-rom drive and I made a bootable USB-flash drive off some version of Ubuntu and it did it for me without too much further ado.

And it's been some time, my desktop doesn't run Windows anymore so I don't recall how I did it but I do believe this page would be the start:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Now in all honesty I would ignore that techspot bit and it's not that I don't believe them but it is too complicated with two sets of instructions so just go with what the folks at Ubuntu are telling us to do on that there download page, apparently the key issue is creating either a Live CD or a Live USB drive, boot with that and it should...
Load up, and you'll be presented with the options.

But just follow the instructions at Ubuntu itself, what I would do.
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Mark Phelps on 2012-01-12
Whatever instructions you follow, do NOT use the option to allow the Ubuntu installer to create the Linux partitions by moving the slider!  Vista, like Win7, is very finicky about its OS partitions being modified by "outside" sources -- like GParted.  While it MAY work OK, it's more likely to result in filesystem corruption, rendering Vista unbootable.

And if that happens, then what? How are you going to get back into using Vista?

BEFORE you do that, use the Vista Disk Management utility to check on the partitions on your drive.  If there are already four of them, you have a LOT of work ahead of you because that is the maximum and you will have to remove one to make room for Ubuntu.

If you do decide to dual-boot, and don't have four partitions, then use the Vista Disk Management utility to shrink the Vista OS partition to make room.  It's very primitive and clumsy to use -- but it won't damage anything.

Then, leave the new space unallocated and use the "Something Else" option in the Ubuntu installer.

---

