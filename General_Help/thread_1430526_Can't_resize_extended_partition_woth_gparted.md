---
title: "Can't resize extended partition woth gparted"
date: 2010-03-15
forum: General Help
---

### Post by GabrielWolff on 2010-03-15
I need to add 2 GB to my Windows partition. 
However, as you can see in the attached screenshot, I'm unable to resize the extended partitin in order to make space for the ntfs partition. 

Why is that?

How can I do it?

G

---

### Post by chewearn on 2010-03-15
Notice the "key" icon next to the swap partitions.  This indicates the partitions are mounted, which also cause the extended partition to be locked.

Right-click on the swap partitions, select "unmount".  This should unlock the extended partition.

---

### Post by leorolla on 2010-03-15
Can't see any screen shot.

Could you post the output of
```
sudo fdisk -l

```
?

---

### Post by GabrielWolff on 2010-03-15
It won't let me make a screenshot but the partition is not mounted. When I right click on the key symbol the option "Unmount" is greyed out.

And anyway I'm with a live CD.

Any other idea why it could be locked?

---

### Post by GabrielWolff on 2010-03-15
> **leorolla said:**
> Can't see any screen shot.

Could you post the output of
```
sudo fdisk -l

```
?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         840     6747268+   7  HPFS/NTFS
/dev/sda2             841       19457   149541052+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
/dev/sda6             841       18709   143532679+  83  Linux
/dev/sda7           18710       19083     3004123+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa2d92c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

Dies it help?

---

### Post by GabrielWolff on 2010-03-15
OK, I swapped off sda5 and sda7, the keythingy disappeared, I can ress the resize button, but the dialog box does not let me change the size. I can't move the partition's borders, neither enter a new size.

Any clue?

G

Notice the greyed out arrows in the dialog

---

### Post by leorolla on 2010-03-15
Best thing is to boot from a LiveUSB, so you can play with you HD unmounted.

Open GParted

Move the right boundary of the extened partition up the whole disk.

Delete the leftmost swap partition.

Extend the right boundary of the EXT4 partition, taking the whole free space.

Then you should have:

[sda1][ sda2 [sda6][sda5] ]

Apply.

---

### Post by GabrielWolff on 2010-03-15
> **leorolla said:**
> Best thing is to boot from a LiveUSB, so you can play with you HD unmounted.

Open GParted

Move the right boundary of the extened partition up the whole disk.

Delete the leftmost swap partition.

Extend the right boundary of the EXT4 partition, taking the whole free space.

Then you should have:

[sda1][ sda2 [sda6][sda5] ]

Apply.

Perfect. Thanks :)

I guess I need only one swap partition? well, I guess I'll notice if it was a grave mistake to delete it :)

---

### Post by mcduck on 2010-03-15
> **GabrielWolff said:**
> OK, I swapped off sda5 and sda7, the keythingy disappeared, I can ress the resize button, but the dialog box does not let me change the size. I can't move the partition's borders, neither enter a new size.

Any clue?

G

Notice the greyed out arrows in the dialog

You must resize the partitions inside the extended partition first. Otherwise there's no room to shrink the partition.

---

### Post by leorolla on 2010-03-15
> **GabrielWolff said:**
> Perfect. Thanks :)

I guess I need only one swap partition? well, I guess I'll notice if it was a grave mistake to delete it :)

You will have to learn how to tell Ubuntu not to use the swap anymore. I don't know how to do it.

---

### Post by hello2012 on 2010-08-24
**[COLOR=black][SIZE=3][FONT=Times New Roman]Of cause there have.[/FONT][/SIZE][/COLOR]**
**[COLOR=black][SIZE=3][FONT=Times New Roman]--Partition Manager.[/FONT][/SIZE][/COLOR]**
**[COLOR=black][SIZE=3][FONT=Times New Roman]This is the best software to finish the operation about resize partition such as [extend partition]("http://www.extend-partition.com/extend-system-boot-partition.html"), shrink partition and so on.[/FONT][/SIZE][/COLOR]**
**[COLOR=black][SIZE=3][FONT=Times New Roman]Not only it can work well, but also has free edition, you can make full use of it.[/FONT][/SIZE][/COLOR]**

---

### Post by brr872002 on 2010-08-24
Just edit your  /etc/fstab  entry related second swap partition

sudo gedit  /etc/fstab

delete  entry related sda5 or sda7  and save the file

---

### Post by leorolla on 2010-08-25
And indeed you can delete both swaps.

I'm a happier person after I found out that we don't actually need swap.

Everytime my computer used swap it was a catastrophe... and I had pelnty of free RAM at everytime it has happened.

---

