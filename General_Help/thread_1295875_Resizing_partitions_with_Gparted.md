---
title: "Resizing partitions with Gparted"
date: 2009-10-20
forum: General Help
---

### Post by kphanee on 2009-10-20
Hi,

I currently have Ubuntu Jaunty installed on a 160GB SATA disk with the following file system configuration:
/dev/sdb1 - / (root partition of type ext3) - 141GB
/dev/sdb2 - linux swap - 5GB

I missed the partitioning step & these partitions were created by installer itself. Can I now resize these partitions using Gparted without effecting the current installation? What specifically I mean is:

1) Can I split the root partition (/) and swap partition into 2 or more partitions now without disturbing the installed ubuntu using Gparted?

2) Can I change the file system type of root partition (/) from ext3 to ext4 without formatting the partition?

If I cannot perform the same with Gparted, is there any other tool which does the same for Jaunty?

Thanks in advance,
Ravi

---

### Post by surfed on 2009-10-20
1) Yes, make sure you do tell gparted NOT TO FORMAT, also you will need to boot with a live cd to be able to do this.
2) Yes, there is a way to migrate but only newly written data takes advantage of ext4, there was a thread on these forums describing how.

---

### Post by egalvan on 2009-10-20
Splitting the large root partition is fairly easy.
Use a LiveCD, because the partition must be un-mounted (not in use) to be able to work with it.

As for swap, a bit more planning is needed.
Moving swap is not a problem, but deleting and creating it can be.
You will run into UUID problems.
They can be solved, but it can be problematic.


And why do you want more than one swap?
A swap partition can be used by any *nix distro...
no need for "one for each".

---

### Post by erfahren on 2009-10-20
> **egalvan said:**
> ...
As for swap, a bit more planning is needed.
Moving swap is not a problem, but deleting and creating it can be.
You will run into UUID problems.
They can be solved, but it can be problematic.

Thats true and it would be best to set up your /etc/fstab file ahead of time to *not* use the UUID before you modify the partitions (the /etc/fstab is a file that Ubuntu uses to mount your partitions)

I can explain what to do for that kphanee, if you'd like

---

### Post by kphanee on 2009-10-20
I don't want to create more than 1 swap partition. My current swap partition is too big (more than 5GB) and I want to reduce its size. For my system with 2GB RAM, anything more than 2GB in swap partition is pure wastage of space. So, I thought of moving that extra space into some partition which I can use.

And yes I would sure like to know what to modify in the /etc/fstab file when resizing my partitions.

---

### Post by Primefalcon on 2009-10-20
easy enough to do just load up a live disk be sure to turn swap off on the swap partition, right click....


resize away, the one thing you may have to do after this is to get the uuid, for some weird reason the uuid on me has a habit of changing when I resize, not much of a hassle though just after your done, and booted your computer from the hard disk. reopen partition editor, you may have install it, if so just run

```
sudo apt-get install gparted
```

then right click on the swap and select information, take note of the uuid and open up /etc/fstab and basically update the uuid, you only need to do this though if the swap isn't mounting after you resize

Note: **NEVER EVER CANCEL A PARTITIONING RESIZE THAT IS IN OPERATION**

---

### Post by erfahren on 2009-10-20
> **kphanee said:**
> ...
And yes I would sure like to know what to modify in the /etc/fstab file when resizing my partitions.
[this page on tuxfiles.org]("http://www.tuxfiles.org/linuxhelp/fstab.html") explains what it does pretty well if you want to check it out, but anyway here's what you do:
first just make a quick backup of it
```

sudo cp /etc/fstab /etc/fstab_back

```
and open it in a text editor (gedit) - we use "gksudo" (or "gksu") here since gedit is a gui application
```

gksu gedit /etc/fstab

```
and you should see something like this (I cut my UUID's down a little here to keep the code box smaller) - the hashes ("#'s") comment the line out so it's not read by the system (those lines are for us humans) 
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=0acc4f90-cda6-4087-b689 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=76bea7c0-d3b8-4ff0-bb66 none            swap    sw              0       0
# (EXTERNAL MEDIA)
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```
yours should be like /dev/sda1 for root and /dev/sda2 for swap (unless you have a factory image partition first) - anyway, replace the UUID's and use the device number instead, like this:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
/dev/sda5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
/dev/sda6 none            swap    sw              0       0
# (EXTERNAL MEDIA)
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```
this is weird but "mount" expects a new line after the last one in the list so put your cursor after the last "0" in the list and hit "enter" (so you have a blank empty line at the end of the file), save the file and close it

this isn't completely necessary but you can remount them to make sure there are no errors
```

sudo mount -a

```
now, if you want to create a new partition(s) it would be easiest to create them at the end of the disk and leave your root and swap partitions in their current order. Once you are done and rebooted you can get your new UUID's by running:
```

sudo blkid

```
and you can insert them back into your /etc/fstab

good luck

---

### Post by kphanee on 2009-10-21
Thanks for all the help. I got the resizing done successfully. :)

---

