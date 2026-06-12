---
title: "swap partition on SSD a bad idea?"
date: 2012-03-07
forum: General Help
---

### Post by Fraoch on 2012-03-07
I just upgraded to an SSD (obviously a HUGE speed increase) and now I'm tweaking it to make sure it stays fast.

I'm used to putting the swap partition on the same drive as the root partition.  However I came across this:

[http://ubuntuforums.org/showpost.php?p=11702911&postcount=8](http://ubuntuforums.org/showpost.php?p=11702911&postcount=8)

[quote=dcstar]The bottom-line seems to be that all of your partitions on a Linux SSD should be EXTx (or whatever else supports TRIM in Linux) otherwise you could virtually have a no-TRIM drive after some time.[/quote]

I enabled TRIM on the ext4 root partition.  There's no way to enable TRIM (the "discard" mount option) on the swap partition as swap partition types don't support it.

Should I move the swap partition off the SSD?

Thanks.

---

### Post by jerome1232 on 2012-03-07
Perhaps you could use a swap file as a sort of workaround

---

### Post by Cheesemill on 2012-03-07
I have my swap on my 1TB hard drive instead of my SSD.

I could actually do without as my system never swaps (8GB RAM), I just have it for the rare occasion I want to hibernate.

---

### Post by Herman on 2012-03-07
I use a small program called [Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/"),( 'swapspace' for short). 
Swap is not needed for system performance as much now as it used to be just a few short years ago when the PCs most of us could afford were underpowered and memory modules were very expensive. Now most computers have adequate RAM.
Nevertheless, the operating system seems laggy if there's no swap area at all.
  Dynamic swap manager creates small swap files automatically on demand. It saves a lot of otherwise wasted disk space compared with using an oversized swap area which is mostly not going to be used.  I imagine it should give another layer of randomization for any wear on top of the wear leveling we would already have built in to the flash memory too. I have not been able to notice any difference in system performance.
A downside is I don't think we can use hibernation with swap Space Manager, or it didn't seem to work for me the last time I tried.
```
sudo apt-get install swapspace
```Then in addition to that I like to adjust swappiness to 10, That tunes the operating system to prefer to us all the RAM first and to only use the swap files as a last resort. Since RAM is much faster than swap, the added benefit is  a small improvement in operating system performance, (your mileage may vary depending on hardware details).  [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") - Ubuntu Community Docs]
       [Linux Performance tuning - vm.swappiness]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html") - unixfoo.blogspot.com
       [What Is the Linux Kernel Parameter vm.swappiness?]("http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/") - Linux Open Source Blog
```
gksudo gedit /etc/sysctl.conf
```Append this line to the bottom of the file,
```
vm.swappiness=10
```The end result is a lean, fast system that can create swap files on demand but hardly ever needs to.

---

### Post by snowpine on 2012-03-07
If you use swap rarely, then it is a non-issue.

If you use swap frequently, then theoretically, you are putting more wear and tear on the SSD. In that case you would benefit from a RAM upgrade or adjustment to your swappiness setting. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

It's worth noting that--all else being equal--modern, high-quality SSD's will probably last longer than a comparable HDD due to the lack of moving parts. (Especially if it is a laptop/netbook.)

---

### Post by Herman on 2012-03-07
:) Hey I'm not on the payroll of any particular hardware manufacturer, nor do I receive any money for advertising hardware products. I'll just say this: The brand of SSD I buy features built in wear leveling of the flash and has had native TRIM for a couple of years now at least, and has a lifetime guarantee.
[http://ubuntuforums.org/showpost.php...11&postcount=8]("http://ubuntuforums.org/showpost.php?p=11702911&postcount=8")
Originally Posted by **dcstar** 					 				
 				[I]> The bottom-line seems to be that all  of your partitions on a Linux SSD should be EXTx (or whatever else  supports TRIM in Linux) otherwise you could virtually have a no-TRIM  drive after some time.


[/I]

---

### Post by Fraoch on 2012-03-07
Thanks for all the replies everyone!

> **Herman said:**
> I use a small program called [Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/"),( 'swapspace' for short). 
Swap is not needed for system performance as much now as it used to be just a few short years ago when the PCs most of us could afford were underpowered and memory modules were very expensive. Now most computers have adequate RAM.
Nevertheless, the operating system seems laggy if there's no swap area at all.
  Dynamic swap manager creates small swap files automatically on demand. It saves a lot of otherwise wasted disk space compared with using an oversized swap area which is mostly not going to be used.  I imagine it should give another layer of randomization for any wear on top of the wear leveling we would already have built in to the flash memory too. I have not been able to notice any difference in system performance.
A downside is I don't think we can use hibernation with swap Space Manager, or it didn't seem to work for me the last time I tried.
```
sudo apt-get install swapspace
```Then in addition to that I like to adjust swappiness to 0, That tunes the operating system to prefer to us all the RAM first and to only use the swap files as a last resort. Since RAM is much faster than swap, the added benefit is  a small improvement in operating system performance, (your mileage may vary depending on hardware details).  [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") - Ubuntu Community Docs]
       [Linux Performance tuning - vm.swappiness]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html") - unixfoo.blogspot.com
       [What Is the Linux Kernel Parameter vm.swappiness?]("http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/") - Linux Open Source Blog
```
gksudo gedit /etc/sysctl.conf
```Append this line to the bottom of the file,
```
vm.swappiness=10
```

The end result is a lean, fast system that can create swap files on demand but hardly ever needs to.

Wow, this is great!

I've carried out both suggestions.  I hardly ever use swap and when my system does it's puzzling because there's usually a few hundred MB of RAM free.  I'd much rather have a program generate a swap file dynamically on demand.  Also the swappiness setting should avoid those rare times I'm using swap and it doesn't look like I really should be.

Should I get rid of my existing swap partition?  Is it as simple as removing the entry in fstab, deleting the partition and merging the empty space into the other partition?

---

### Post by Cheesemill on 2012-03-07
> **Fraoch said:**
> Is it as simple as removing the entry in fstab, deleting the partition and merging the empty space into the other partition?

Yep. That will do it.

---

### Post by Fraoch on 2012-03-07
> **Herman said:**
> :) Hey I'm not on the payroll of any particular hardware manufacturer, nor do I receive any money for advertising hardware products. I'll just say this: The brand of SSD I buy features built in wear leveling of the flash and has had native TRIM for a couple of years now at least, and has a lifetime guarantee.

While I'm very pleased with the speed of my new Crucial M4, it looks very much like it desperately needs TRIM:

[http://www.anandtech.com/show/4253/the-crucial-m4-micron-c400-ssd-review/2](http://www.anandtech.com/show/4253/the-crucial-m4-micron-c400-ssd-review/2)

It's simple enough to do, just enter "discard" into the fstab mount options.  For kicks I also used "noatime" here to reduce writes.  I was thinking of making a tiny HOWTO for this but it's so trivial I'd feel silly.

---

### Post by Fraoch on 2012-03-07
> **Cheesemill said:**
> Yep. That will do it.

Thanks!

---

### Post by dcstar on 2012-06-26
Here is an update on the whole TRIM/SSD swap issue.

The Linux kernel has had "Discard" support for swap since 2.6.29, and basically uses TRIM automatically for all swap functions. If you don't have a device that actually supports the "Discard" commands then apparently there is no problem.

This man page has some of the info:

[http://linux.die.net/man/2/swapon](http://linux.die.net/man/2/swapon)

and this page explains it a bit more:

[http://danielsmedegaardbuus.dk/2011-02-15/swap-partitions-and-ssds-a-beautiful-match/](http://danielsmedegaardbuus.dk/2011-02-15/swap-partitions-and-ssds-a-beautiful-match/)

Bottom-line seems to be that Linux supports SSDs for swap use.

---

