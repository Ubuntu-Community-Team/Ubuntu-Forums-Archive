---
title: "command to switch to different hard drive?"
date: 2010-01-16
forum: General Help
---

### Post by bmesta on 2010-01-16
hello,

can someone please tell me the command to switch to a different hard drive. I have multiple hard drives in my computer. One called storage and the other one called filesystem. I would like to know how can i access the Storage hard drive via the terminal

---

### Post by forsaken_pariah on 2010-01-16
If it's not already mounted, you should be able to run this

```
sudo mount /dev/sdb* /media/storage
cd /media/storage
```where /dev/sdb* is the partition that you want to mount.

---

### Post by bmesta on 2010-01-16
> **forsaken_pariah said:**
> If it's not already mounted, you should be able to run this

```
sudo mount /dev/sdb* /media/storage
cd /media/storage
```where /dev/sdb* is the partition that you want to mount.
thanks a lot bro. thats exactly what i need it but how do i go back now? do i have to do the mount thing eveyrtime i want to access teh Storag hard drive?

---

### Post by Zimmer on 2010-01-16
If the storage disk is already mounted at boot by fstab then you need only cd to its mount point.
You can either find its mount point in Nautilus by looking at the folder properties and noting the location (something like /media/disk) so cd /media/disk  would take you to the root of that drive.

The 'simple' answer if it is not mounted at boot is to add disk mounter to your Gnome panel and mount it from there and see where it gets put! 

(you can mount it on any location you wish to create, if you so wish, but the manual for the mount command is around 1700 lines and requires a lot of reading to grasp the options you might need for your particular disk).
old tutorial here re mounting and fstab...
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by forsaken_pariah on 2010-01-16
I haven't really tried this myself so I can't promise it'll work, but you can try this:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Hope this helps!

---

### Post by Mickser_52 on 2010-01-16
Do you have many hard drives or one hard drive with many partitions? 

You could try the following.

open terminal
then type: **cd** / (space before /)
then type:**ls** (to list folders and files in directory)
in the list you should see one called **media**
type **cd media** (to select that directory)
type **ls** (again to list contents of media)
is your partition **storage** listed there?

if so type** cd storage**
and then **ls** to list files stored there.

To return type **cd /** again
then **cd /home/"your username"**

---

### Post by jamesisin on 2010-01-16
I wrote a nice post about adding additional drives to Ubuntu.  I think you'll find the information useful:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

Let me know (here or there) if you have any questions.

---

