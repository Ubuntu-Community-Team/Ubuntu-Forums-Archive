---
title: "Having Problems Mounting Ext4 External Hard Drive"
date: 2010-07-05
forum: General Help
---

### Post by giddyup306 on 2010-07-05
Hello everyone, here's the deal.  I wanted to make a clone of my drive, so I tried the ole sudo dd if=/dev/sda1 of=/dev/sdg1 trick, but first I formatted the drive to the Ext4 format.  I wish I would have understood that format a little more before I decided to format it that way.  Now I can't access my drive at all.  I read almost everything on the net about manually mounting it, but almost everything was in Fat, NTFS, or Ext3/2 format.  I even read the Ubuntu documentation.  I don't know if it's because my drive is in Ext4 format, or if I'm just not doing something right.  As you can see in the following picture, it recognizes the drive, yet I am unable to mount it.  I am trying to access the 160 GB drive.  I even tried to see if Windows would recognize it.  No go.  Today while lurking in the Ubuntu Forums I found a way to make a live .iso of my system (which I think is awesome).  So now I want to reformat my drive and use it as storage once again.  I think I will restore it to NTFS.  I thought that the Ext4 format would work better in Linux (which I was wrong), but now I need Windows to recognize it as well, and it needs to be able to store files bigger than 4 GB (unless you have a suggestion on what to format it as).  

If you could help a brotha out, I'd appreciate it.   

[IMG]http://i169.photobucket.com/albums/u219/giddyup306/hd.png[/IMG]

---

### Post by giddyup306 on 2010-07-05
I think I'm getting closer.  I think all I need to do is find out how to make a mount point for Ext4 (all the other ones I tried gave me an error saying that the filesystem was incorrect).

```
giddyup306@giddyup306-desktop:~$ sudo mount -t ext4 /dev/sdg /media/media
mount: mount point /media/media does not exist

```

The /dev/sdg part is right, but I don't know how to make the mount point (the /media/media was in the example, so I decided I'd try it).

---

### Post by aust77 on 2010-07-05
Very close indeed. To make a mount point, do this:
```
sudo mkdir /DIRECTORY/MOUNTPOINT NAME
```
I prefer to make my mount directories within /mnt, I believe that is where they are supposed to go.

---

### Post by aust77 on 2010-07-05
This might be a bit unrelated, but perhaps it might offer you some assistance. I mount an external Window hard drive every time I install a new Ubuntu install using this code:
```
sudo mount -t smbfs -O username=USERNAME //MOUNTPOINTIP/SHARENAME /mnt/MONUTPOINTDIR
``` 
Of course thats using smbfs to mount the Windows drive, so I'm sure you'll need to tweak it a bit. Definitely use -O before inputting the other details (I believe O stands for other, and don't forget, it's the letter in upper case, not the number zero).

I hope this helps you.

Cheers,


aust77

---

### Post by giddyup306 on 2010-07-05
> **aust77 said:**
> Very close indeed. To make a mount point, do this:
```
sudo mkdir /DIRECTORY/MOUNTPOINT NAME
```I prefer to make my mount directories within /mnt, I believe that is where they are supposed to go.


Thanks for the help.  I tried that thinking that I did something wrong tho.

```
giddyup306@giddyup306-desktop:~$ sudo mount -t ext4 /dev/sdg /mnt/160external
mount: wrong fs type, bad option, bad superblock on /dev/sdg,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

giddyup306@giddyup306-desktop:~$ 

```

Is there a chance that my HD went south, or am I still missing something?

---

### Post by btindie on 2010-07-05
You're getting closer! The drive is /dev/sdg but the PARTITION is /dev/sdg1. So try
```
 
sudo mount -t ext4 /dev/sdg1 /mnt/160external

```

---

### Post by giddyup306 on 2010-07-05
> **btindie said:**
> You're getting closer! The drive is /dev/sdg but the PARTITION is /dev/sdg1. So try
```
 
sudo mount -t ext4 /dev/sdg1 /mnt/160external

```
Okay so rather than going into my computer I need to go into /mnt/160external and I can use this like any other external drive correct?  The reason why I'm asking is because I want to make sure that the system files on this drive can be deleted so I can use it for storage (I'm scared of deleting the system files on my machine).  I've had a couple scares in Linux.

Thanks everyone for the help!

EDIT:

It will let me view the files, but that's all.  How can I change this?  Is it a permissions issue?  I ran into this one time before, but I don't remember how I fixed it. *doh*

Okay I got my issue 100% fixed!

sudo gksu nautilus

---

### Post by btindie on 2010-07-05
If you go to My Computer does the partition not show up as one you can browse? I think usually they do. If not, and you want to access it every time you can add an entry to */etc/fstab* to have it mounted at startup.
```
sudo gedit /etc/fstab
```
and add a line like
```
/dev/sdg1     /mnt/160external     ext4      defaults        0    0
```

---

### Post by giddyup306 on 2010-07-05
It doesn't show up under Computer, but it does show up under /mnt.  It will not however let me click on it to unmount it.  I looked at my fstab before I mounted the drive, and the ext4 part wasn't there before...  



```
proc            /proc           proc    defaults        0       0
UUID=0d6a073d-a565-42de-a7b7-2c71164238bd /               ext4    errors=remount-ro 0       1
UUID=7d026e40-37fd-4998-a902-34df49f5d4a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I added: 

```
/dev/sdg1     /mnt/160external     ext4      defaults        0    0
```

To the bottom, saved, and still nothing changed. *shrugs*

---

### Post by btindie on 2010-07-05
/etc/fstab lists the partitions that should be mounted by the system at startup. It won't automatically have an entry there so nothing will *change* by having an entry there. In future you can mount/umount it with
```
sudo mount /mnt/160external
```
you don't need to specify the drive or anything as the system already knows about it from *fstab*.
 
You won't be able to unmount it by right clicking unmount as it was originally mounted by root.
 
Something you may want to try to get the system to pick it up. Firstly umount the drive
```
sudo umount /mnt/160external
```
Comment out the fstab entry you just added by placing a # in front of the line. Then use *pmount-hal* to mount it
```
pmount-hal /dev/sdg1
```
If that didn't work then try
```
sudo pmount-hal /dev/sdg1
```
(I don't have access to a suitable box at the minute to check the correct syntax.)

---

### Post by giddyup306 on 2010-07-05
No wonder why it wouldn't unmount.  I used unmount instead of umount. *doh*

Right now my computer is busy making a backup (it's 10% done after almost an hour).  I will report later.  ;)

---

