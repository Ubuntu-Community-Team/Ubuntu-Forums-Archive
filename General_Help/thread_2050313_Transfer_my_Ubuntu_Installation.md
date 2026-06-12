---
title: "Transfer my Ubuntu Installation"
date: 2012-08-30
forum: General Help
---

### Post by GravityDead on 2012-08-30
Okay, let's start
I have Ubuntu 12.04 in my DELL N4110 Laptop as a DUAL BOOT (not WUBI)
I customized it, made it perfect for me :)

But now, I have to remove it cause I need a partition.
Note- I already had 3 PRIMARY partitions by default, and then ubuntu became the 4th.

and now I've come to know that one can only make 4 partitions
[IMG]http://s14.postimage.org/vf5av8x0h/Workspace_1_002.png[/IMG]
As you can see from the screenshot, I have only one option, if I need one more partition, then I have to delete the Ubuntu partition, cause I cannot remove windows 7...

So I was wondering if anyone could tell me a method to transfer my UBUNTU INSTALLATION "as-it-is" to a USB Pen drive (16GB) or to an external HDD (500Gigs but without formatting it) so that when I create a bigger logical(extended) partition, I can install it again...
n if that is not possible, so to a permanent Ubuntu USB or HDD or may be WUBI install.

n yeah, see if you can tell me a method that doesn't involve downloading heavy files as my monthly data cap just finished today and now I am left with 256kbps speed only :(

by the way I have acronis true image live CD(of course I have windows 7 along side), if that can help :D

---

### Post by cortman on 2012-08-30
> **GravityDead said:**
> Okay, let's start
I have Ubuntu 12.04 in my DELL N4110 Laptop as a DUAL BOOT (not WUBI)
I customized it, made it perfect for me :)

But now, I have to remove it cause I need a partition.
Note- I already had 3 PRIMARY partitions by default, and then ubuntu became the 4th.

and now I've come to know that one can only make 4 partitions
[IMG]http://s14.postimage.org/vf5av8x0h/Workspace_1_002.png[/IMG]
As you can see from the screenshot, I have only one option, if I need one more partition, then I have to delete the Ubuntu partition, cause I cannot remove windows 7...

So I was wondering if anyone could tell me a method to transfer my UBUNTU INSTALLATION "as-it-is" to a USB Pen drive (16GB) or to an external HDD (500Gigs but without formatting it) so that when I create a bigger logical(extended) partition, I can install it again...
n if that is not possible, so to a permanent Ubuntu USB or HDD or may be WUBI install.

n yeah, see if you can tell me a method that doesn't involve downloading heavy files as my monthly data cap just finished today and now I am left with 256kbps speed only :(

by the way I have acronis true image live CD(of course I have windows 7 along side), if that can help :D

[Remastersys]("http://www.remastersys.com/") or [Clonezilla]("http://clonezilla.org/").

---

### Post by oldfred on 2012-08-30
Welcome to the forums.

You screen shot is not showing any LInux partitions. It that supposed to show your install? Are you sure it is not wubi then?

You can shrink the Windows partition and move extended left into the unallocated. Then inside the extended you can make as many partitions as you want. You would have to unmount the extended. The little key icon says it is mounted.

If you want to shrink Windows use the Windows tools to shrink it and reboot several times, so it can run chkdsk and update to its new size. But do not create partitions with Windows. Use gparted or the installer to create new partitions.

---

### Post by dcstar on 2012-08-31
> **oldfred said:**
> Welcome to the forums.

Your screen shot is not showing any LInux partitions.
.........

The screenshot does not have the Extended partition expanded, Linux is probably in it along with Swap.

The OP can put as many partitions as it likes in the Extended Partition, provided there is space.

---

### Post by GravityDead on 2012-08-31
> Welcome to the forums.

You screen shot is not showing any LInux partitions. It that supposed to show your install? Are you sure it is not wubi then?

You can shrink the Windows partition and move extended left into the unallocated. Then inside the extended you can make as many partitions as you want. You would have to unmount the extended. The little key icon says it is mounted.

If you want to shrink Windows use the Windows tools to shrink it and reboot several times, so it can run chkdsk and update to its new size. But do not create partitions with Windows. Use gparted or the installer to create new partitions.


nah it's not WUBI
can you see that one 41GB extended partition in the end
my Ubuntu is installed there.

Yeah I can shrink my windows partition but it will shrink from the "right end"
in fact I tried this before posting this query
but the extended partition does not give my the option to extend its size from its left side :p
Haha I have no idea whether you will understand me or not :rolleyes:

So in short I have to delete my last partition so that I can shrink my windows partition by a bigger amount which can handle both, my ubuntu and and my other needs :D

> Remastersys or Clonezilla.
I guess I'll have to use one of them at last
sigh, will take hours to download them
and yeah My ubuntu is a bit more than 4 GB
so don't you think I will face problems there too
as I read somewhere is there is something 4 GB limit on cloning using remastersys
I'm not sure about clonezilla process

AND finally, the swap thing
I have no idea about that
but yeah my last partition which is extended type and has my Ubuntu
has two sub-partitions in it
one is bigger 37 gigs and another is very small, only 4 Gigs :-k

---

### Post by oldfred on 2012-08-31
I did not even know you could collapse the display & I did not scroll right to see the Linux partitions.

You definitely can move extended partition left into the unallocated space after shrinking the Windows NTFS partition.
It will not let you do it until after you shrink the Windows partition in Windows, do not use gparted to shrink the Windows partition and reboot several times to make sure Windows runs chkdsk and has updated itself to its new size.

Swap of 4GB is fine.  It needs to be the same size as RAM in GiB only if you want to hibernate.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by GravityDead on 2012-08-31
> You definitely can move extended partition left into the unallocated space after shrinking the Windows NTFS partition.
It will not let you do it until after you shrink the Windows partition in Windows, do not use gparted to shrink the Windows partition and reboot several times to make sure Windows runs chkdsk and has updated itself to its new size.

Have a look, I have again shrink'ed my C drive and this time using Windows tool as you suggested and then chkdsk too
My result with unallocated 35 GB -
[IMG]http://s19.postimage.org/m4lr0iaxf/dev_sda_GParted_002.png[/IMG]

as I told earlier I cannot expand my Ubuntu Partition because the unallocated space is at the left side of my ubuntu partition and to be able to expand it, unallocated space has to be at its right side

This is the menu I get when R-clicking the /dev/sda5, i.e my ubuntu partition.
[IMG]http://s19.postimage.org/qf0ew3g0j/Menu_001.png[/IMG]

So I guess I will have to remove my partiton at last :(

---

### Post by oldfred on 2012-08-31
Please attach screen shots with the little paperclip icon in the edit panel above you message. There are too large as posted.

The little key icons say the partitions are all mounted. You have to use a liveCD so partitions are not mounted. And even a liveCD usually mounts swap so you have to click on swap and right click swap-off to unmount it. Then you will be able to edit the extended partition and your Linux partitions.

---

### Post by GravityDead on 2012-08-31
> And even a liveCD usually mounts swap so you have to click on swap and  right click swap-off to unmount it. Then you will be able to edit the  extended partition and your Linux partitions.Right now posting from a Live-CD

ohh you the man, oldfred =D> \\:D/:guitar: [-o< :cool:
respect

Seriously man, expanding my partition right now :D
You know, I was so frustrated that I was about to delete the partition

thank you oldfred
big time

and of course, one more thanks for your quick replies c-:
:popcorn::KS


------------------------------------------------- THREAD CLOSED  ---------------------------------------------------

---

### Post by oldfred on 2012-08-31
Your are welcome & glad it worked. :)

---

