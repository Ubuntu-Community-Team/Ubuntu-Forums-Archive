---
title: "Change partitions after installation"
date: 2011-09-18
forum: General Help
---

### Post by X_Splinter on 2011-09-18
Hello guys.

I justed installed Ubuntu 11.04 in my laptop and found that in this version it didnt asked if I wanted to make the partitions.

So the Ubuntu is installed in a single partition (+ a swap partitions of course)

The thing is I want a partition for /home only.

I can still do it without losing my Ubuntu installation?

---

### Post by TeoBigusGeekus on 2011-09-18
Fire up gparted, create a partition to be used as home, add an entry for it in your fstab, copy everything from your current home folder to it, give
```
sudo mount -a
```
and you're done.

---

### Post by garvinrick4 on 2011-09-18
I would reinstall and first make partitions in gparted for installations / and /home and swap. Then use "something else" I believe my mind keeps thinking manual install like old way. The last selection at installation anyway. (Sorry should no exact wording but memory
just failed me)
Put your / in partition number you made for it. sda[COLOR=Red]x[/COLOR] and /home and swap. Use / mount point and ext4 for / partition and ext4 and /home for /home partition and swap for swap. Tick format in / and /home
[COLOR=Red]x[/COLOR] being the number it is in gparted.
Put grub in sda if using internal drive. Not sda1 or sda2 but sda

Do this with a live cd in 'gparted" (install cd using Try Ubuntu)
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
Installation directions:
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
Below another gparted (says dual boot but has more graphic's on gparted)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

# Only takes a few minutes to make partitions and install might as well get off to clean start. ( just my suggestion, post2 has using fstab if comfortable with fstab below is link)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by X_Splinter on 2011-09-18
> **TeoBigusGeekus said:**
> Fire up gparted, create a partition to be used as home, add an entry for it in your fstab, copy everything from your current home folder to it, give
```
sudo mount -a
```
and you're done.

But the partion with root mounted covers all the disk, I need non-formated space in my drive to creat a new partion.

Is there a way to shrink the root partion?

---

### Post by TeoBigusGeekus on 2011-09-18
> **X_Splinter said:**
> But the partion with root mounted covers all the disk, I need non-formated space in my drive to creat a new partion.

Is there a way to shrink the root partion?

Ah! Then you need to boot with a live cd/usb and do the task.
After you've finished, don't issue the mount command I posted, just reboot.

---

### Post by owiknowi on 2011-09-18
yes you can shrink a root partition with gparted (pmagic) too.

if you consider a fresh install, i would at this point for that matter, here some basic and some more advanced ways of doing so:
[http://www.owiknowi.org/tips.html](http://www.owiknowi.org/tips.html)

---

### Post by garvinrick4 on 2011-09-18
Do you by chance have a alternate CD That will not go into a Live Cd?
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
any which way I am sure you will get this worked out so enjoy your Ubuntu.
I have got in the habit of working with the beginner section so much I write everything out.
Did not really mean to talk like you have never seen Linux before, you so have 3 years in Forum.

---

