---
title: "re permisions on files in mp3 player"
date: 2011-08-18
forum: General Help
---

### Post by CoyoteUK5 on 2011-08-18
Hi

REcently I been having some problems with when I attach my mp3 player.

THanks to those who helped me with deleting the files but now a new problem has come up.
Now for some reason the files go there from my external hardrive but they show a padlock on their icons and in file manager it shows the drive but there is a x sign on it. 
Now this sounded like a permision issue so I rightclicked it and got the dialogue box up and went to permisions under my name it said read and write but in the group it said access none and others none, I tried to change this but it keeps resetting itself.
I wonder if anyone has any ideas how I can do change this:confused:

---

### Post by frankbooth on 2011-08-18
It sounds like it gets mounted with the "wrong" permissions.

If this is the case, we could change the way it mounts by editing it's existing entry in */etc/fstab*, or we could make a new entry.

To view your *fstab*, open a terminal and type:
```

nano /etc/fstab

# or if you prefer a text editor with GUI:

mousepad /etc/fstab

```

If you're unsure, paste your *fstab* file wrapped with [code] tags.

---

### Post by CoyoteUK5 on 2011-08-18
Thanks frank
I must I am quite nervous of using the terminal I do not what I did last time but I had to reload xubuntu last time.
Anyway I put the query in the terminal and here is the result.
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bf3d4273-820c-49ab-a310-da375b4b91aa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2070a85f-110c-4036-a5ee-5cd91d5b2fc5 none            swap    sw              0       0
It looks like the error was while I was installing but I do not know if I can rectify or not.
Any help would be useful

Thanks

---

### Post by tredegar on 2011-08-18
Your MP3 player isn't being mounted by **fstab**
It is mounted by **udev**

Please, plug it in.
Find out where it is mounted (Probably as /media/player or similar)
Tell us the permissions/ owner of that directory by posting the output of
```
ls -l /media/
```

---

### Post by frankbooth on 2011-08-18
You do not seem to have an entry for you mp3-player in *fstab*. Lets see if we can solve your problem by making one...

**1)** First we need to find out what the UUID for your mp3-player is. There are several ways to do this, but here is one...
[LIST]
[*]Open 'Disk Utility' (pretty sure you have it in Xubuntu, make sure your mp3 is connected)
[*]Click on your device and see where it's mounted (should look something like '/dev/sdX')
[*]Also note what kind of format it is formatted in (the rest of the guide will assume it's FAT32)
[*]Open the terminal and type:
[/LIST]
```

ls -l /dev/disk/by-uuid/

```
This should give you a result that looks somewhat like this:
```

lrwxrwxrwx 1 root root 10 2011-08-18 18:40 **364f55cd-a9f8-4e47-934e-aeec63ae9b7d** -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-08-18 18:58 **B775-3929** -> ../../sdb1
lrwxrwxrwx 1 root root 10 2011-08-18 18:40 **e4452bff-2801-49bb-b375-2657330a8c38** -> ../../sda5

```
*The bold numbers are UUID's.*

**2)** We need to make a folder where we mount the mp3-player:
```

sudo mkdir /media/mp3

```
*You can name the folder something else if you'd like to.*

**3)** Lets edit *fstab*:
```

sudo mousepad /etc/fstab

```
Add this line to *fstab* *(Only if your mp3 is formatted in FAT, if not - ask)*:
```

UUID=?????????????   /media/mp3  vfat   rw,user,noauto  0   0

```

Your drive should now mount with the proper permissions, unless I've done a mistake somewhere ;).

---

### Post by CoyoteUK5 on 2011-08-24
I am sorry I have been away for a while but I now seem to have another problem but please be patient with me as I do have more questions

---

### Post by flurospar on 2011-08-24
Often, this can be enough:
```

cd /media/mount_point
sudo chmod a=rwx *.mp3

```

---

