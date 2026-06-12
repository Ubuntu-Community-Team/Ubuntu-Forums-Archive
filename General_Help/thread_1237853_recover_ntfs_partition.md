---
title: "recover ntfs partition"
date: 2009-08-11
forum: General Help
---

### Post by rafaelcoelho on 2009-08-11
hi.. I had a ntfs partition occupying all my 160GB hd
I first used ntfsresize to resize it to 100GB and then used fdisk to resize the partition and to create another partition with the rest of the space
but I think after I deleted and created the new partition, neither mount or ntfsresize recognize the resized ntfs (100GB) anymore

my commands was like:

sudo ntfsresize --size 100GB /dev/sda1
sudo fdisk /dev/sda1
# deleted the partition
# created one partition to like 110GB, set active and fs type 7 (HPFS/NTFS)
# created another partition with the rest of the space, fs type 7 too
w -- to apply the changes to the partition table

then I tryed

sudo mount -t ntfs /dev/sda1 /media/win

and I got an error:
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
...

what can I do to recover my ntfs partition?

thanks

---

### Post by iswear on 2009-08-11
You could try using the ubuntu recovery remix cd. Its not a graffical interface but it worked for me. When you put it in just type sudo testdisk, and then choose your hd and then the rest us pretty simple.

---

### Post by Tuvok41 on 2009-08-12
Dont know if that will work for you but it did work for me when one of my ntfs drive wouldnt mount, I didn't want to force mount it as I had it all full of valuable data.
I used this to get it back to mount :

```
sudo ntfsfix /dev/sdf1
```

change /dev/sdf1 to /dev/sda1 since it is the partition you want to fix. 
You might have to install the ntfsfix in order to make it work.

```
sudo apt-get install ntfsprogs
```

Well I hope this will do the trick, if so it will be my first to successfully help someone, finally giving back what I got from others.

---

### Post by Tuvok41 on 2009-08-12
> **rafaelcoelho said:**
> hi.. I had a ntfs partition occupying all my 160GB hd
I first used ntfsresize to resize it to 100GB and then used fdisk to resize the partition and to create another partition with the rest of the space
but I think after I deleted and created the new partition, neither mount or ntfsresize recognize the resized ntfs (100GB) anymore

my commands was like:

sudo ntfsresize --size 100GB /dev/sda1
sudo fdisk /dev/sda1
# deleted the partition
# created one partition to like 110GB, set active and fs type 7 (HPFS/NTFS)
# created another partition with the rest of the space, fs type 7 too
w -- to apply the changes to the partition table

then I tryed

sudo mount -t ntfs /dev/sda1 /media/win

and I got an error:
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
...

what can I do to recover my ntfs partition?

thanks
So did you fix it yet?

---

### Post by rafaelcoelho on 2009-08-12
> **Tuvok41 said:**
> So did you fix it yet?

not yet.. I am having some problems with the disc drive too, so I cant boot my notebook with the ubuntu live CD or ubuntu recover remix by now to try yours suggestions
but as soon as I try it I'll post the results here

thanks

---

### Post by rafaelcoelho on 2009-08-12
Tuvok41, I tryied ntfsfix but it didn't work

actually, I think I messep up my entire hd :/
I dumped the beggining of my hd and partition and they are almost all zeroed

---

### Post by rafaelcoelho on 2009-08-13
I finally recovered it..
I dumped my hd again and found the "NTFS" signature at address 1MB, then I just used fdisk and created a partition that started at this address (  sector 2048 ) and it worked
I dont know if I did something wrong before or if there was a better way to recover it, but it worked anyway..

---

### Post by Tuvok41 on 2009-08-14
I think it doesn't need to be mounted to use ntfsfix, it usually fixes the issue of not being able to mount it because Windows has not released it yet. If it is something else then this fix may not work for your problem. Glad you recovered it :-)

---

