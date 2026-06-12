---
title: "Installing a ms os"
date: 2009-09-26
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-09-26
I currently have a multi boot system, I want to install ms 2k but it will overwrite my existin grub mbr, is there a simple way to restore my grub after installing ms2k?

---

### Post by edouardp on 2009-09-26
I usually restore grub with
[Super grub  disk]("http://www.supergrubdisk.org/")
It's a bootable CD that will prompt you with options to restore grub. Their is an automatic option which will search your disk for a grub entry, and restore it on the mbr

You can also do this manually with an ubuntu live cd (more tricky):
- boot on the live cd
- open a terminal window
you will now need to mount your ubuntu root ( / )
```
sudo mkdir /media/root
sudo mount -t ext3 /dev/sda1 /media/root
```
Replace /dev/sda1 with your ubuntu root (sudo fdisk -l to see available partitions)
```
sudo mount -o bind /dev /media/root/dev
```
this will make your devices visible in the chroot jail (see next line)
```
sudo chroot /media/root
grub-install /dev/sda
```
again, replace /dev/sda with the path to your hard disk. This will reinstall grub on the mbr. The last thing you need to do is to add the windows entry to /boot/grub/menu.lst. There are examples on how to do that in the file.

---

### Post by Feelin_froggy8877 on 2009-09-26
After searching a bit, found something that seems a bit too easy, haha  [http://www.youtube.com/watch?v=mjdTduleSbY](http://www.youtube.com/watch?v=mjdTduleSbY). will that do?

---

### Post by edouardp on 2009-09-26
I wasn't aware of this way to restore grub, but it seems to work great :p

---

### Post by Feelin_froggy8877 on 2009-09-26
Whoops, didnt notice your reply. TY, BTW.

---

### Post by Feelin_froggy8877 on 2009-09-26
That will recover my grub boot menu as it exists now? (either way)

---

### Post by Feelin_froggy8877 on 2009-09-26
If ms is told to install on a second disk out of (sda, sdb, and sdc) Will it still overwrite the mbr of the first disk, or will it write to the second disk's mbr (sdb)? The reason I ask is, after checking up a bit, I decided to go ahead and try the install. After the initial setup process and restart, the mbr (first disk, sda) appears not to be touch at all. And cannot access the win2k install.

---

### Post by benerivo on 2009-09-26
I think a Windows install to secondary drive (sdb) will write the mbr to that drive, rather than sda. You can still configure grub to boot in to the sdb OS.

---

### Post by Feelin_froggy8877 on 2009-09-27
That is true. (wrote the mbr to the second disk where it was installed to.)  I just  had to add the ...

title		Microsoft Windows 2000
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1
                       ...to my menu.lst. Worked like a charm.

---

### Post by Feelin_froggy8877 on 2009-09-27
Ok, Well after thinking everything was all good, I tried to boot win xp, And it seems win 2k messed up something there. Xp was unbootable. So I reinstalled Xp (first disk)  and went ahead with the instructions...

sudo grub

grub> find /boot/grub/stage1
(hd0,4)

grub> root (hd0,4)

grub> setup (hd0)

Everything seemed to work, ending result was "succeeded" But, did not write grub to the mbr. I am now booting w/ "sgd" Booting partition. I will now attempt your first suggestion. Does that have to be done from the live cd? Or can I run from within my installed ubuntu?

---

### Post by Feelin_froggy8877 on 2009-09-27
HA, cant win for loosing. The method in the first reply worked fine (not sgd) But now after reinstalling xp, the mbr of my second disk was over written and now win 2k wont boot, boots to xp either way I go now (unbelievable) Anyway edouardp's first post is the way to go.

---

### Post by HermanAB on 2009-09-27
Hmm, once you got it going again, consider installing VMware or Virtualbox and save yourself from this head-ache.  Multi-boot is so 20th Century...
;)

---

### Post by Feelin_froggy8877 on 2009-09-27
Thanx, always willing to try something new. This is the first I heard of those. Are they pretty straight forward in use?

---

### Post by PaulReaver on 2009-09-27
what I do to install multiple os's was when installing a new os unplug every other hard disk apart from the one I wanted to install on.

I've got gentoo, ubuntu, xp, and vista each its own hard disk.

grub chainloader is my friend

---

### Post by Feelin_froggy8877 on 2009-09-27
That's actually what I was gonna do next before I reinstalled win 2k. I used to do that to be (sure) I wasn't going to format/delete the wrong partition. That's before I got a lil more confident on partitioning.Right now I have, ubuntu, xp, antix, puppy, crunchbang and saybyon, well antix was replaced w/ win 2k:) But again. thankx for the reply :-) I'm already checking out virtual box...installing xp now, pretty cool s***

---

### Post by oldfred on 2009-09-28
If you have mutiple operating systems see this site on using chainbooting for 145 different systems on 2 hard drives. It is now a little old but still current on how to plan and use:

[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Herman on chainloading:
[http://members.iinet.net.au/~herman546/p15.html#2._Chainloader](http://members.iinet.net.au/~herman546/p15.html#2._Chainloader)

---

### Post by Feelin_froggy8877 on 2009-09-28
I might decide to go with the virtualbox for xp, the only thing is,I would want to delete the xp partiton all together. Ubuntu and xp are on the same disk. Xp is on the primary partition and Ubuntu is on the extended partition. Since Ubuntu is on the extended part, can I safely delete the primary partition and resize for ubuntu?

---

### Post by Feelin_froggy8877 on 2009-09-30
Bump?

---

### Post by oldfred on 2009-09-30
You can delete the partition, all partitions can be in the extended. But if you modify partitions entries in menu.lst based on partition location and in fstab for mounting will all have to be updated. It can be done, but best if you know what you are doing.
I suggest keeping the partition and making it a data only partition.

---

