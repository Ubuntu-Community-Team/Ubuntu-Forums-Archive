---
title: "Getting rid of an Ubuntu Partition"
date: 2010-07-19
forum: General Help
---

### Post by Mercenary(FH) on 2010-07-19
So quick recap. Basically I have a Windows 7 and an Ubuntu partition on a 360gb or so hard drive.

It uses GRUB Loader to switch between the 2. I've recently Acquired a laptop that I'd rather put Ubuntu on, and leave my Desktop as my Windows 7 machine (since i really only use linux for programming anyways)

How or what would be the best way to completely wipe Ubuntu from my Desktop and get all my used Hard drive space back?


Thanks :)

(and do i need to uninstall GRUB to? if so i'll need to know how to do that as well)

---

### Post by etdsbastar on 2010-07-19
> **Mercenary(FH) said:**
> So quick recap. Basically I have a Windows 7 and an Ubuntu partition on a 360gb or so hard drive.

It uses GRUB Loader to switch between the 2. I've recently Acquired a laptop that I'd rather put Ubuntu on, and leave my Desktop as my Windows 7 machine (since i really only use linux for programming anyways)

How or what would be the best way to completely wipe Ubuntu from my Desktop and get all my used Hard drive space back?


Thanks :)

(and do i need to uninstall GRUB to? if so i'll need to know how to do that as well)

Don't worry, Its very easy.

You want ubuntu to be wiped out ok. Do it as below:


[LIST=1]
[*]Insert your windows boot cd and select repair on the first screen i mean to say you have to remove your grub first.
[*]Refer for help in [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[*]Now after performing the steps in above no. 2, start your windows 7 and then Open the Control Panel (All Items view), and  click on the **Administrative Tools** icon. then close the Control  Panel window.
[*]Click on **Computer Management** in Administrative Tools, then close  the Administrative Tools window.
[*]In the left pane under **Storage**, click on **Disk Management**.
[*]In the middle pane, right click on the partition which says (Unknown or Raw, you can easily distinguish by watching it)  that you want to delete  and click on **Delete Volume**.
 **[COLOR=red]NOTE:[/COLOR]*** If the partition is a **logical  partition**, then you will need to delete the free space again to have  it as unallocated space* or create a newone after deleting all linux/ubuntu partitions.
[*]Close the Computer Management window.
[/LIST]
Hope this helps.

---

### Post by Mercenary(FH) on 2010-07-19
> **etdsbastar said:**
> Don't worry, Its very easy.

You want windows to be wiped out ok. Do it as below:


[LIST=1]
[*]Insert your windows boot cd and select repair on the first screen i mean to say you have to remove your grub first.
[*]Refer for help in [http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[*]Now after performing the steps in above no. 2, start your windows 7 and then Open the Control Panel (All Items view), and  click on the **Administrative Tools** icon. then close the Control  Panel window.
[*]Click on **Computer Management** in Administrative Tools, then close  the Administrative Tools window.
[*]In the left pane under **Storage**, click on **Disk Management**.
[*]In the middle pane, right click on the partition which says (Unknown or Raw, you can easily distinguish by watching it)  that you want to delete  and click on **Delete Volume**.
 **[COLOR=red]NOTE:[/COLOR]*** If the partition is a **logical  partition**, then you will need to delete the free space again to have  it as unallocated space* or create a newone after deleting all linux/ubuntu partitions.
[*]Close the Computer Management window.
[/LIST]
Hope this helps.

Whoa. i want Ubuntu to be wiped, NOT windows

---

### Post by techunit on 2010-07-19
Well We need to know which partition has GRUB on it...

---

### Post by borth92 on 2010-07-19
I think its fairly obvious the Ubuntu partition has the GRUB installation. Thats going to be a serious problem...you are gonna need to find a way to reinstall the windows boot loader before you worry about deleting ubuntu...because if you remove ubuntu with grub still as the default bootloader then the computer will try to load grub when you turn t on and you will get an error message every time and will not be able to boot into windows without reinstalling grub from a ubuntu livecd

---

### Post by etdsbastar on 2010-07-20
> **Mercenary(FH) said:**
> Whoa. i want Ubuntu to be wiped, NOT windows

That is what I am saying, where did you find that Windows is gonig to be wiped out, I said to remove the ext3/4 partition from Disk Management.

---

### Post by -kg- on 2010-07-20
> **etdsbastar said:**
> That is what I am saying, where did you find that Windows is gonig to be wiped out, I said to remove the ext3/4 partition from Disk Management.

Probably where I did...at the very beginning of your previous post:

>  Originally Posted by etdsbastar  View Post
Don't worry, Its very easy.

[COLOR="Red"]**You want windows to be wiped out ok.**[/COLOR] Do it as below:

I was a little taken aback when I read that, myself...enough that I didn't read the rest until after I read your second post.

:p

---

### Post by etdsbastar on 2010-07-20
> **-kg- said:**
> Probably where I did...at the very beginning of your previous post:

I was a little taken aback when I read that, myself...enough that I didn't read the rest until after I read your second post.

:p

I am extremely sorry for the mistake I have done, I have rectified the post accordingly. Thanks for telling me.

---

### Post by Mercenary(FH) on 2010-07-20
It's NP. i was just a bit confused so I didn't want to do anything before I knew for sure.

oh and Ubuntu installed GRUB on it......if that is what a previous user was asking.


edit: Ok everything worked. and I deleted the partition so it says "169.20 GB Unallocated"
(I had to delete it twice, it said logical after I deleted it once)

How do I go about....like "adding" that space to my partition in windows? or is that impossible

edit2: NM i durped. I figured it out. lol

---

### Post by reklan on 2010-07-20
This will show you how to extend the volume..

[http://www.sevenforums.com/tutorials/2670-partition-volume-extend.html](http://www.sevenforums.com/tutorials/2670-partition-volume-extend.html)

---

### Post by etdsbastar on 2010-07-20
> **Mercenary(FH) said:**
> It's NP. i was just a bit confused so I didn't want to do anything before I knew for sure.

oh and Ubuntu installed GRUB on it......if that is what a previous user was asking.


edit: Ok everything worked. and I deleted the partition so it says "169.20 GB Unallocated"
(I had to delete it twice, it said logical after I deleted it once)

How do I go about....like "adding" that space to my partition in windows? or is that impossible

edit2: NM i durped. I figured it out. lol

Right click on the unallocated space and select add partition.

---

### Post by erbeesr on 2010-09-05
the Grub is always on the first partition, usually C:.  The best way to remove Linux partitions is by using Acronis boot manager.  Delete the linux partitions and then resize the Windows partition back the way it was before.  Use a Windows 98 boot disk and run FDISK/MBR.  That will resotore the Master Boot Record and Windows will boot up normally.

---

