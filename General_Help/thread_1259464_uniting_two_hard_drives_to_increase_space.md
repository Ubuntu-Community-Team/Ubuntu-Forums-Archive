---
title: "uniting two hard drives to increase space"
date: 2009-09-06
forum: General Help
---

### Post by justborn on 2009-09-06
Actually i have a 80GB hard drive(i came with my comp,5 years ago) ,which is almost full(94.8 %) and i cannot feed in any data on it anymore.i have an another ,spare 80GB hard drive. can any one suggest me a  way to unite them both,so that my data is stored on the second one after the first is comlpetely full.

---

### Post by NoaHall on 2009-09-06
Move every personal file (not system files) to the other hard drive. So stuff like Pictures, and maybe music (but you'll have to link your media player programs to them on the other drive)

---

### Post by wojox on 2009-09-06
Do you have the second drive installed and recognized (ie. master/slave)?

---

### Post by justborn on 2009-09-06
> **NoaHall said:**
> Move every personal file (not system files) to the other hard drive. So stuff like Pictures, and maybe music (but you'll have to link your media player programs to them on the other drive)

i thought of that ,but will just connecting the second hard drive to the secondary slave work,or do i have to formate it ,or do some sort of configuration.

---

### Post by justborn on 2009-09-06
> **wojox said:**
> Do you have the second drive installed and recognized (ie. master/slave)?

no i actually have windows 7 beta on it and its rests in my cpu disconnected.

---

### Post by Stone_Soup on 2009-09-06
You have a couple of options justborn. If you want you can always set a RAID array. As you have (2) 80G hard drives you can set a RAID 0 and span the drives to create (1) larger logical 160G drive. There are pros and cons to this setup:

**Pros:**
If you stripe it you will get increased performance and create one larger drive out of two smaller ones.

**Cons:**
Without parity (or a third drive to record parity) if one drive fails then all of your data is lost because each drive has part of the data.

**My suggestion: **What I did was create a JBOD type of setup where my OS is on one drive and my data on the other. That way if my OS fails, becomes corrupt, or if I want to install multiple OS then I can just work on that drive and leave the data on my second drive alone and re-access it when I have everything up to speed (think of it as having internal removable media that you never really remove). Just make sure your data drive is formated in a way that is compatible with the largest number of OS (I use vfat) so that you can access it irregardless of what you install on the first drive.

---

### Post by justborn on 2009-09-06
> **Stone_Soup said:**
> You have a couple of options justborn. If you want you can always set a RAID array. As you have (2) 80G hard drives you can set a RAID 0 and span the drives to create (1) larger logical 160G drive. There are pros and cons to this setup:

**Pros:**
If you stripe it you will get increased performance and create one larger drive out of two smaller ones.

**Cons:**
Without parity (or a third drive to record parity) if one drive fails then all of your data is lost because each drive has part of the data.

**My suggestion: **What I did was create a JBOD type of setup where my OS is on one drive and my data on the other. That way if my OS fails, becomes corrupt, or if I want to install multiple OS then I can just work on that drive and leave the data on my second drive alone and re-access it when I have everything up to speed (think of it as having internal removable media that you never really remove). Just make sure your data drive is formated in a way that is compatible with the largest number of OS (I use vfat) so that you can access it irregardless of what you install on the first drive.
refering to consequence,i dont think that there can be any serious data loss on linux.(jus because i haven't come across),but still to be on the safer side ,i'll take ur suggestion.

but i jus opened the box i discoverd that the slve is connected to the cd drive so what shoud i do,can i not connet the master to two had drives?(with the help of some simple hardware i suppose)

and thanks for the brief explaination

---

### Post by fela on 2009-09-06
Make a filesystem on the spare drive, create a folder on it, automount the spare drive (with /etc/fstab), and create a link from a directory on the old drive to the directory that you created on the new drive.

If you want a truly seamless 'disk across 2 disks' config then you could use JBOD or RAID 0 if your hardware supports it.

---

### Post by justborn on 2009-09-06
> **fela said:**
> Make a filesystem on the spare drive, create a folder on it, automount the spare drive (with /etc/fstab), and create a link from a directory on the old drive to the directory that you created on the new drive.

If you want a truly seamless 'disk across 2 disks' config then you could use JBOD or RAID 0 if your hardware supports it.

please can u tell me the procces in detail(step wise is guess). i am not aware of it



u can suggest me a link,i thing that will do fine.


edit:
and will the process involve the connection of the second drive to the slave,coz it is connected to the cd drive ,as i earlier mentioned?

---

### Post by justborn on 2009-09-06
i jus connected the second hard drive ,it is split in four partions(i has winodows 7 on it ).i wanna to erase all the stuff and re-unite all the the partions.

what software should i use?

---

### Post by gnicko on 2009-09-06
> **justborn said:**
> refering to consequence,i dont think that there can be any serious data loss on linux.(jus because i haven't come across),but still to be on the safer side ,i'll take ur suggestion.

but i jus opened the box i discoverd that the slve is connected to the cd drive so what shoud i do,can i not connet the master to two had drives?(with the help of some simple hardware i suppose)

and thanks for the brief explaination

I'm sorry...if you could clear something up...Is the second hard drive hooked up, recognized, "useable" right now? Does the computer know that it's there?

Thanks.

---

### Post by justborn on 2009-09-06
> **gnicko said:**
> I'm sorry...if you could clear something up...Is the second hard drive hooked up, recognized, "useable" right now? Does the computer know that it's there?

Thanks.


ya the computer does recognize it.

---

### Post by fela on 2009-09-06
> **justborn said:**
> i jus connected the second hard drive ,it is split in four partions(i has winodows 7 on it ).i wanna to erase all the stuff and re-unite all the the partions.

what software should i use?

You should use cfdisk to do this.

These instructions assume that the hdd isn't the one with ubuntu on it. If it is, then you'll have to run this from a liveCD and reinstall Ubuntu once you're done. Of course, **remember to backup your data in case you make a mistake. It's as easy as using the wrong harddisk and you've wiped all your data on that harddisk.**
From the command line:

```
sudo fdisk -l
```

Now decide which harddisk (e.g. /dev/sda) is the one you want to repartition. From now on I assume the harddisk is /dev/sda. Remember to change it to whatever is in your setup. Now, run:

```
sudo cfdisk /dev/sda
```

Now delete all your partitions on that drive from Cfdisk's interface, and make a new one. Change the partition type if necessary, and then apply and quit.

Now, here is a short list of a few filesystems:

[LIST=1]
[*]ext2
[*]ext3
[*]ext4
[*]xfs
[*]jfs
[*]ntfs
[*]vfat
[/LIST]

The first 5 filesystems are in type 'Linux', and I recommend using the second, third or fourth. The second is very stable, as is the fourth, the fourth is faster than the second, and the third is also quite fast but quite young (so we aren't sure of its stability). You can read up on filesystems on places like wikipedia if you like. I recommend a Linux filesystem as they work better with Linux, only use the other two if you have to be able to access them from windows. **ext4 is only officially supported in Ubuntu 9.04 or later.**

The last 2 filesystems are NTFS and FAT16/32 respectively. Now, depending on what you chose in cfdisk (Linux/NTFS/FAT16/FAT32), run:

```
sudo mkfs.fstype /dev/sda1
```

Where 'fstype' is a filesystem type from the list.

And now you can mount your filesystem on whatever directory you like. An idea actually, is to mount it at a directory inside your home directory so it looks like it's part of your home directory. You could do something like this:

```
mkdir ~/Storage
sudo mount /dev/sda1 ~/Storage
```

That should mount your new filesystem. To unmount it, run (and it is umount, not unmount):

```
sudo umount /dev/sda1
```

To have it automatically mount when Linux boots, add a line such as this (assuming the filesystem is ext4) to the bottom of the file /etc/fstab:

```
/dev/sda1 /home/username/Storage ext4 defaults 0 0
```

HTH

---

### Post by justborn on 2009-09-06
> **fela said:**
> You should use cfdisk to do this.

These instructions assume that the hdd isn't the one with ubuntu on it. If it is, then you'll have to run this from a liveCD and reinstall Ubuntu once you're done. Of course, **remember to backup your data in case you make a mistake. It's as easy as using the wrong harddisk and you've wiped all your data on that harddisk.**
From the command line:

```
sudo fdisk -l
```

Now decide which harddisk (e.g. /dev/sda) is the one you want to repartition. From now on I assume the harddisk is /dev/sda. Remember to change it to whatever is in your setup. Now, run:

```
sudo cfdisk /dev/sda
```

Now delete all your partitions on that drive from Cfdisk's interface, and make a new one. Change the partition type if necessary, and then apply and quit.

Now, here is a short list of a few filesystems:

[LIST=1]
[*]ext2
[*]ext3
[*]ext4
[*]xfs
[*]jfs
[*]ntfs
[*]vfat
[/LIST]

The first 5 filesystems are in type 'Linux', and I recommend using the second, third or fourth. The second is very stable, as is the fourth, the fourth is faster than the second, and the third is also quite fast but quite young (so we aren't sure of its stability). You can read up on filesystems on places like wikipedia if you like. I recommend a Linux filesystem as they work better with Linux, only use the other two if you have to be able to access them from windows. **ext4 is only officially supported in Ubuntu 9.04 or later.**

The last 2 filesystems are NTFS and FAT16/32 respectively. Now, depending on what you chose in cfdisk (Linux/NTFS/FAT16/FAT32), run:

```
sudo mkfs.fstype /dev/sda1
```

Where 'fstype' is a filesystem type from the list.

And now you can mount your filesystem on whatever directory you like. An idea actually, is to mount it at a directory inside your home directory so it looks like it's part of your home directory. You could do something like this:

```
mkdir ~/Storage
sudo mount /dev/sda1 ~/Storage
```

That should mount your new filesystem. To unmount it, run (and it is umount, not unmount):

```
sudo umount /dev/sda1
```

To have it automatically mount when Linux boots, add a line such as this (assuming the filesystem is ext4) to the bottom of the file /etc/fstab:

```
/dev/sda1 /home/username/Storage ext4 defaults 0 0
```

HTH

i did it the easier way i used gparted,fast and good,but i cannot transfer files from the first to the second.i shows me an error

---

### Post by gnicko on 2009-09-06
> **justborn said:**
> i did it the easier way i used gparted,fast and good,but i cannot transfer files from the first to the second.i shows me an error

Is it a permissions/ownership error? Or is it having to do with mounting the filesystem?

---

### Post by justborn on 2009-09-06
i formatted the new drive ext4,and then then ext3,but it's only detectable and i cannot transfer content.

---

### Post by justborn on 2009-09-06
> **gnicko said:**
> Is it a permissions/ownership error?

yes sir.

---

### Post by fela on 2009-09-06
> **justborn said:**
> yes sir.

Boot up ubuntu.

Open a terminal.

```
cd /path/to/mounted/directory

sudo chown -R $USER .
```

Now tell me if it works.

---

### Post by justborn on 2009-09-06
> **fela said:**
> Boot up ubuntu.

Open a terminal.

```
cd /path/to/mounted/directory

sudo chown -R $USER .
```

Now tell me if it works.

```
arpit@arpit-desktop:~$ cd /media/disk
arpit@arpit-desktop:/media/disk$ sudo chown -R $USER
[sudo] password for arpit: 
chown: missing operand after `arpit'
Try `chown --help' for more information.
```

---

### Post by fela on 2009-09-06
> **justborn said:**
> ```
arpit@arpit-desktop:~$ cd /media/disk
arpit@arpit-desktop:/media/disk$ sudo chown -R $USER
[sudo] password for arpit: 
chown: missing operand after `arpit'
Try `chown --help' for more information.
```

You didn't notice the little . after $USER (it wasn't a typo, don't assume that people make typos ;)). The . character in bash means the current directory.

EDIT: the command may take a while depending on how much data there is on the disk. You could try it without the -R option first. If you still get problems run it again with the -R option.

---

### Post by justborn on 2009-09-07
yes it is working now,but is the ownerchange permanant?
 do i have to still enter the password everytime i wanna open the drive.
and dont want the media drive icon to be displayed on the desktop.so can u help.

---

### Post by fela on 2009-09-07
> **justborn said:**
> yes it is working now,but is the ownerchange permanant?
 do i have to still enter the password everytime i wanna open the drive.
and dont want the media drive icon to be displayed on the desktop.so can u help.

Yes, the permissions change is permanent, at least until something or someone else changes the permissions on it.

---

### Post by justborn on 2009-09-08
pls can someone tell me, how do i enable auto-mount for the second disk.i don't wanna enter in the password every time  to mount the media disk.

---

### Post by fela on 2009-09-08
> **justborn said:**
> pls can someone tell me, how do i enable auto-mount for the second disk.i don't wanna enter in the password every time  to mount the media disk.

You have to create the correct entry under /etc/fstab. An example is:

```
/dev/sda2 /media/disk2 ext4 defaults 0 0
```

This assumes that /dev/sda2 is the device file for the partition in question. Running sudo fdisk -l will list all partitions and devices currently on your system.

The example mounts it at /media/disk2, this directory could be anywhere on your system (although make sure to use a directory not used by anthing else, ie. a custom directory, to avoid problems). Also, make sure the directory exists ((sudo) mkdir /path/to/directory) before adding the fstab entry.

The filesystem for the example is ext4, change this to whatever filesystem you used.

There are options that you can add in the defaults bit, but generally just defaults should be fine.

When you've created the entry in fstab and saved the file, run

sudo mount -a

to test it out (make sure the drive isn't already mounted of course :lol:).

---

