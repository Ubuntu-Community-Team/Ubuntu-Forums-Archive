---
title: "Total file capacity 100% how do I clear it?"
date: 2011-06-08
forum: General Help
---

### Post by Nexialist on 2011-06-08
[CENTER]My total file capacity is reading at 100% 
but my total file system usage is only 3.8%

used: 5.5 gb available: 138.3gb

here is my Df reading: 

[http://paste.ubuntu.com/621582/]("http://paste.ubuntu.com/621582/")


I cleaned up some disk space with bleachkit, but it's still reading at 100% I checked my computer hard disk in disk utility and they seem to be fine, I cleaned up some unneeded stuff, so what I am I doing wrong? (btw I am totally new too linux)

Help is greatly appreciated!

Also when I went to disk utility it seems I have a second 80 gig hard disk that was not in use, but how would I set that up? I clicked partition, but that didn't didn't seem to help my capacity at all.
[/CENTER]

---

### Post by ajgreeny on 2011-06-08
> **Nexialist said:**
> [CENTER]My total file capacity is reading at 100% 
but my total file system usage is only 3.8%

used: 5.5 gb available: 138.3gb

here is my Df reading: 

[http://paste.ubuntu.com/621582/](http://paste.ubuntu.com/621582/)


I cleaned up some disk space with bleachkit, but it's still reading at 100% I checked my computer hard disk in disk utility and they seem to be fine, I cleaned up some unneeded stuff, so what I am I doing wrong? (btw I am totally new too linux)

Help is greatly appreciated!

Also when I went to disk utility it seems I have a second 80 gig hard disk that was not in use, but how would I set that up? I clicked partition, but that didn't didn't seem to help my capacity at all.
[/CENTER]

Where are you finding that 100% figure?

The df readings show that you have used 5.5GB out of 71GB, not 138GB.

Can you show us the output of ```
sudo fdisk -l
``` which will show all your partitions, not just those that are mounted at that moment.

---

### Post by Nexialist on 2011-06-08
> **ajgreeny said:**
> Where are you finding that 100% figure?

The df readings show that you have used 5.5GB out of 71GB, not 138GB.

Can you show us the output of ```
sudo fdisk -l
``` which will show all your partitions, not just those that are mounted at that moment.

[CENTER]here is the Fdisk:
[http://paste.ubuntu.com/621627/]("http://paste.ubuntu.com/621627/")

the thing is the disk usuage analyzer is saying I am at 100% but I don't understand why it would be.[/CENTER]

---

### Post by RoyLongbottom on 2011-06-08
[FONT=Verdana][SIZE=2]It seems to me that the 100% indicates that the whole disk is formatted and allocated for partitions. I see that using Applications, Accessories, Disk Usage Manager on a nearly empty disk.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

---

### Post by Nexialist on 2011-06-08
> **RoyLongbottom said:**
> [FONT=Verdana][SIZE=2]It seems to me that the 100% indicates that the whole disk is formatted and allocated for partitions. I see that using Applications, Accessories, Disk Usage Manager on a nearly empty disk.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

[CENTER]So what do I need to do?
I am new to this.
[/CENTER]

---

### Post by ajgreeny on 2011-06-08
You are misunderstanding how the disk usage analyser works, as it will report the base filesystem as 100% wherever you start, and then just shows how the components of that filesystem use the space that is in use, for example if you choose /home as the base, that will be 100%, and the diagram will show the %ages of that used by each of the subfolders, Documents, Downloads, Music etc etc.  Very useful if you realise what is shown, but very confusing if you don't.

Your fdisk output shows a second disk, sdb, with one partition using the whole disk which is probably not being mounted or used by ubuntu at the moment.  If you now also run ```
sudo blkid
```in terminal and show the output from that it will be possible to give you a line to add to /etc/fstab in order to mount that disk at boot time and use as a data partition.

---

### Post by Nexialist on 2011-06-08
> **ajgreeny said:**
> You are misunderstanding how the disk usage analyser works, as it will report the base filesystem as 100% wherever you start, and then just shows how the components of that filesystem use the space that is in use, for example if you choose /home as the base, that will be 100%, and the diagram will show the %ages of that used by each of the subfolders, Documents, Downloads, Music etc etc.  Very useful if you realise what is shown, but very confusing if you don't.

Your fdisk output shows a second disk, sdb, with one partition using the whole disk which is probably not being mounted or used by ubuntu at the moment.  If you now also run ```
sudo blkid
```in terminal and show the output from that it will be possible to give you a line to add to /etc/fstab in order to mount that disk at boot time and use as a data partition.
[CENTER]here is the output:
[http://paste.ubuntu.com/621640/]("http://paste.ubuntu.com/621640/")

Thanks for helping me! I understand how the disk usage works, but installing this new hard disk would be nice as well if you do not mind helping me :][/CENTER]

---

### Post by ajgreeny on 2011-06-08
Ok, here goes.

1.  Make a new folder in /home as a mountpoint for your storage partition with the commands ```
 mkdir storage
```
2.  Just in case something goes wrong, backup /etc/fstab with ```
sudo cp /etc/fstab /etc/fstabbackup
```3.  Open /etc/fstab as root so you can edit it with ```
gksu gedit /etc/fstab
```4.  Copy and add the 2 lines below to /etc/fstab
```
# /dev/sdb1 storage partition
UUID="ee751784-45df-4d4e-8b83-bc0ef389cadb" /home/*username*/storage ext4 defaults,relatime 0 2
```5.  In terminal run the command ```
sudo mount -a
```and you should be able to read and write to it easily in /home/username/sdb1.

Good luck.  Come back again if anything doesn't work.

---

### Post by dFlyer on 2011-06-08
Could you please stop centering your output as I find it very distracting.

---

### Post by Nexialist on 2011-06-09
> **ajgreeny said:**
> Ok, here goes.

1.  Make a new folder in /home as a mountpoint for your storage partition with the commands ```
 mkdir storage
```
2.  Just in case something goes wrong, backup /etc/fstab with ```
sudo cp /etc/fstab /etc/fstabbackup
```3.  Open /etc/fstab as root so you can edit it with ```
gksu gedit /etc/fstab
```4.  Copy and add the 2 lines below to /etc/fstab
```
# /dev/sdb1 storage partition
UUID="ee751784-45df-4d4e-8b83-bc0ef389cadb" /home/*username*/storage ext4 defaults,relatime 0 2
```5.  In terminal run the command ```
sudo mount -a
```and you should be able to read and write to it easily in /home/username/sdb1.

Good luck.  Come back again if anything doesn't work.

Thank you!:D

---

### Post by Nexialist on 2011-06-09
> **dFlyer said:**
> Could you please stop centering your output as I find it very distracting.

Oh sorry, won't happen again.

---

### Post by ajgreeny on 2011-06-09
> **Nexialist said:**
> Thank you!:D
So all is now working?

---

