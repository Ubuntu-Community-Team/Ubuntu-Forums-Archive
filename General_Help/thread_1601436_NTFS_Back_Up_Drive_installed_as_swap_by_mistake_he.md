---
title: "NTFS Back Up Drive installed as swap by mistake help!!"
date: 2010-10-20
forum: General Help
---

### Post by F12OST on 2010-10-20
When installing ubuntu I selected my back up NTFS partition as a swap drive for ubuntu and now i cant access my files so does anybody have a solution to revert the partition back to be Labelled as NTFS so i can access my files please thanks

---

### Post by Hero_Lief on 2010-10-20
Hate to say it, but if it was labelled as a swap drive, I think it's completely reformatted. No files are there; they've been erased. Someone correct me if I'm wrong.

---

### Post by F12OST on 2010-10-20
i'm pretty sure they there coz it wasn't formatted

---

### Post by F12OST on 2010-10-20
any1 pls

---

### Post by MooPi on 2010-10-20
Can you start gparted and give us a screen shot of the drive setup ?
Or you can post the results of ```
sudo fdisk -l
```
If you could do both that would be great.

---

### Post by Mark Phelps on 2010-10-20
That command is a lowercase L, not a one.

---

### Post by F12OST on 2010-10-20
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11ac3300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+  83  Linux
/dev/sda2           12749       38912   210162299+   f  W95 Ext'd (LBA)
/dev/sda5           12749       38912   210162298+  82  Linux swap / Solaris

---

### Post by F12OST on 2010-10-20
Here a screen shot of gparted 

[[IMG]http://content.imagesocket.com/thumbs/Screenshot749.png[/IMG]](http://imagesocket.com/view/Screenshot749.png) [IMG]http://imagesocket.com/view/Screenshot749.png[/IMG][IMG]http://imagesocket.com/view/Screenshot749.png[/IMG]

---

### Post by MooPi on 2010-10-20
Your screenshot seems corrupted. Sorry now I see it. Highlight the swap partition with your mouse and right click to view the menu. There should be a swapoff selection to choose. After the swap is turned off you can try a couple of things. First you can attempt to mount the partition, to see if any of your files are there. Another option would be to reboot and see if the system recognizes the file system as the original fat file system. This is new territory for me as I've never seen this before. Possible third option is to boot a Live Ubuntu CD to see if the file system can be viewed.

---

### Post by F12OST on 2010-10-20
I done that swap off thing yday and i cant seem to find how to mount it , I did try a live cd but no luck properly coz I dont know what im doin

---

### Post by MooPi on 2010-10-20
I was hoping that the files would be there, but the truth is the partition has been formated as swap and the data may be lost. Can you restart gparted and give us another view of the screenshot to see if the labels have changed. Maybe you can change the partitions  label.There is a chance we may be able to manually mount.

---

### Post by F12OST on 2010-10-20
the label the same how u change the label with format ? and mount it ?

---

### Post by coffeecat on 2010-10-20
> **MooPi said:**
>  but the truth is the partition has been formated as swap and the data may be lost.

Not necessarily. If the filesystem itself has not been damaged it may be possible to get the NTFS partition back by editing the partition table. But it essential that the OP use the swap partition not at all. The trouble is the hard drive install of Ubuntu will mount the swap partition automatically on bootup with its fstab entry and the live CD will automatically detect the swap partition and mount it.

@F12OST, I have no experience or expertise in restoring lost partitions, but I believe the app you need for this in Ubuntu is Testdisk. From the package description for Testdisk:

```
TestDisk checks the partition and boot sectors of your disks.
 It is very useful in recovering lost partitions.
```I suggest you do **nothing** until someone with expertise can tell you how to use Testdisk. The more you use Ubuntu whether on the hard drive or from a live CD, the more likely you are to write to the swap partition and damage the original filesystem, which will still be there (hopefully) but at present inaccessible.

---

### Post by MooPi on 2010-10-20
Do not format !!!!!!!!!!!
Try this in terminal
 ```
sudo mkdir /media/myswap
```
```
sudo mount /dev/sda2 /media/myswap
```
See if your files are now located in /media/myswap

---

### Post by F12OST on 2010-10-20
frost@vd2:~$ sudo mount /dev/sda2 /media/myswap
mount: you must specify the filesystem type

---

### Post by coffeecat on 2010-10-20
@F12OST, [SIZE=6]STOP![/SIZE]

Read my earlier post. You are in a deep hole with your data at risk and you are digging an even deeper one.

---

### Post by MooPi on 2010-10-20
> **coffeecat said:**
> @F12OST, [SIZE=6]STOP![/SIZE]

Read my earlier post. You are in a deep hole with your data at risk and you are digging an even deeper one.

Time to listen to coffecat. I'm just taking shots in the dark :(

---

### Post by F12OST on 2010-10-20
:(

---

### Post by coffeecat on 2010-10-20
> **F12OST said:**
> :(

Sorry to have to shout to get your attention, but I believe and hope that you may still yet recover that partition. :) I hesitate to tell you how to use testdisk as I do not have enough experience, but I have seen and read enough threads to make me believe it is worth trying.

I suggest you wait and see if someone joins the thread who can talk you through it. You could also search the forum for relevant threads. There is a forum member, srs5694, whose posts you might want to search for. What he doesn't know about filesystems and partitions isn't worth knowing. I've learnt a lot just by reading his posts. I believe there was a thread recently in which he helped someone with testdisk.

---

### Post by F12OST on 2010-10-20
> **coffeecat said:**
> Sorry to have to shout to get your attention, but I believe and hope that you may still yet recover that partition. :) I hesitate to tell you how to use testdisk as I do not have enough experience, but I have seen and read enough threads to make me believe it is worth trying.

I suggest you wait and see if someone joins the thread who can talk you through it. You could also search the forum for relevant threads. There is a forum member, srs5694, whose posts you might want to search for. What he doesn't know about filesystems and partitions isn't worth knowing. I've learnt a lot just by reading his posts. I believe there was a thread recently in which he helped someone with testdisk.

Hehe it all good, I'll check his post out and see what I can find

---

### Post by oldfred on 2010-10-20
I never have had to use testdisk but some links on more info.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by piratebill on 2010-10-20
Also I suggest downloading (with a separate computer mind you) backtrack 4 livecd.  It should have testdisk on it.  Boot off the cd choose forensics mode (this will not mount your swap partition and thus not overwrite the data on it).

---

### Post by F12OST on 2010-10-20
yeah I got me a BT4 somewhere, thanks for the links [oldfred]("http://ubuntuforums.org/member.php?u=852711")

---

