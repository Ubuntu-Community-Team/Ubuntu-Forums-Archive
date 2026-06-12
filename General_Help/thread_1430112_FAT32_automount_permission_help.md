---
title: "FAT32 automount permission help"
date: 2010-03-14
forum: General Help
---

### Post by hazelnutz18 on 2010-03-14
Hi - I have firefox and thunderbird access from Ubuntu and windows. I do this by keeping the profiles on a separate hdd. I can manually mount the drive while in Ubuntu and there is no issue. I've tried to edit fstab to auto mount the drive on boot but cant get the permissions right for firefox/thunderbird to have access. The drive is fat32 and I've tried changind the permissions in a bunch of ways but just cant get it. The drive mounts fine but user doesn't have rw access no matter what I try. Any help would be appreciated.

"Normal fstab"

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                         0  0  
# / was on /dev/sda2 during installation
UUID=e0fe3606-a9ad-493a-8a34-265d9a105238  /               ext4         errors=remount-ro                0  1  
# swap was on /dev/sdb3 during installation
UUID=bec4c299-2289-4597-a913-2badac51c23a  none            swap         sw                               0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8            0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8         0  0 





A few of my many attempts and none of the following have worked:

/dev/sdb1                                  /media/sdb1     vfat         auto,users,rw,exec		 0  0

/dev/sdb1                                  /media/sdb1     vfat         defaults,auto,uid=1000,dmask=027,fmas=137		 0  0

/dev/sdb1                                  /media/sdb1     vfat         defaults,auto,uid=1000,umask=000		 0  0

I feel that is something specific with fat that I just don't know about... I've also tryed using pySDM to no avail.

Thanks!

---

### Post by blazemore on 2010-03-15
try ```
chown username: /media/sdb1
```
Substitute your username for "username" and don't forget the colon

---

### Post by sisco311 on 2010-03-15
Use the UUID of the partition instead of the device name. Type:
```
sudo blkid -o value -s UUID /dev/sdb1
```to get the UUID.

& in the fstab entry use your login name instead of the numeric user id:
```
UUID=**insert-the-UUID-here**    /mnt/sdb1    vfat    defaults,uid=**username**,gid=**username**,dmask=0027,fmask=0137    0    0
```

NOTE: You don't have to reboot to remount the partition. Unmount it (if it's mounted):
```
sudo umount /dev/sdb1
```
Edit the fstab file, then mount the partitions mentioned in fstab:
```
sudo mount -a
```

---

### Post by oldfred on 2010-03-15
I think sisco311 has it right. 

I also share my profiles and up until Karmic had them in FAT, I have since converted to NTFS. This was my entry back then that worked. share was my mount point into my home

# Entry for /dev/sda4 :
UUID=46CD-C9B2 /home/fred/share vfat user,auto,fmask=0111,dmask=0000 0 0

---

### Post by hazelnutz18 on 2010-03-15
Thanks for all your suggestions and help but it hasn't worked yet.

blazemore:
Changing ownership didnt throw back any errors but it didn't take either.

sisco311:
setting /mnt/sdb1 as the mount point didnt work - It said the mount point does not exit. It only works with /media/sdb1. If I drive /dev/sdb1 it says the mount point is not a directory. When it moutns with /media/sdb1 - the permissions are still not allowing access.

oldfred:
I tried your method and got it to mount - then tried to manually change permissions on the folder. The permissions just wont take. Root will not give up access ;-)

Is there a way to make it a publically shared folder or something with no restrictions whatsoever and work backwards from there.

I really appreaciate everyone's help!

-------------------

I apologise - I'm an idiot - once I got it to mount at /home/hazelnutz18/Share I had to go back and edit my firefox profile to look for the new folder. It works! Thanks to everyone for their help - I wanted to leave the reply above in case it will help someone else. Thanks again!!

---

### Post by Morbius1 on 2010-03-15
You cannot change permissions or ownership of a windows filesystem using chmod or chown or through nautilus. That's only for linux filesystems. You take ownership and set permissions in fstab.

What's not real clear in your description is whether or not you ever created the mount point /mnt/sdb1.
 
From sisco311:
> UUID=**insert-the-UUID-here**    /mnt/sdb1    vfat    defaults,uid=**username**,gid=**username**,dmask=0027,fmask=0137    0    0Did you do this:

[B] sudo mkdir /mnt/sdb1

[/B][COLOR=Blue]EDIT: Never mind. I clearly don't have a clue what's going on here. Thought it was a mounting issue and now it looks like a samba sharing issue - or maybe not [/COLOR]

---

### Post by Toshibawarrior on 2010-03-28
> **sisco311 said:**
> Use the UUID of the partition instead of the device name. Type:
```
sudo blkid -o value -s UUID /dev/sdb1
```to get the UUID.

& in the fstab entry use your login name instead of the numeric user id:
```
UUID=**insert-the-UUID-here**    /mnt/sdb1    vfat    defaults,uid=**username**,gid=**username**,dmask=0027,fmask=0137    0    0
```

NOTE: You don't have to reboot to remount the partition. Unmount it (if it's mounted):
```
sudo umount /dev/sdb1
```
Edit the fstab file, then mount the partitions mentioned in fstab:
```
sudo mount -a
```

Thank you VERY much! I'm tinkering with Lucid BETA1 and I forgot to backup my old fstab...so I lost my "permission-enabled-automount". I remembered how to make a fat32 partition automount, but I forgot all about the permissions thing...but now it WORKS!! Thanks again!

---

