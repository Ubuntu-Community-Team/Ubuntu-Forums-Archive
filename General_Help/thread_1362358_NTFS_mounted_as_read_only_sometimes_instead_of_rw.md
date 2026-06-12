---
title: "NTFS mounted as read only sometimes instead of rw"
date: 2009-12-23
forum: General Help
---

### Post by kapiladhanvi on 2009-12-23
I have Ubuntu 9.10 installed and while I mostly enjoy using it, I am consistently having issues with my auto mounted FAT32 drives. Sometimes when I restart my system, and I try to access the mounted FAT32 volume it takes a long time to read the contents of a directory and then marks the file system as read only. 

Inspite of unmounting and remounting the FAT32 filesystem, it still mounts as a read-only system from them on. The only solution I have is to do a complete system restart which is painful when I am in the middle of something. 

Below is the relevant section of fstab detailing the mounting for the volume - 
```
/dev/sda6 /media/d_drives vfat users,gid=1000,uid=1000,fmask=0002,dmask=0002,defaults,rw,nosuid,flush 0 0
```

I hardly boot into Windows and so its not like I have a unclean shutdown of windows. I usually close the lid of my laptop when I am done with my work and have setup my preferences to do a shutdown when lid is closed since Ubuntu takes forever to resume from a hibernated session. 

can you please help me resolve this ? 

Thanks for all your help.
Dhanvi

---

### Post by dcstar on 2009-12-23
> **kapiladhanvi said:**
> I have Ubuntu 9.10 installed and while I mostly enjoy using it, I am consistently having issues with my auto mounted NTFS drives. Sometimes when I restart my system, and I try to access the mounted NTFS drive it takes a long time to read the contents of a directory and then marks the file system as read only. 

Inspite of unmounting and remounting the NTFS filesystem, it still mounts as a read-only system from them on. The only solution I have is to do a complete system restart which is painful when I am in the middle of something. 

Below is the relevant section of fstab detailing the mounting for the NTFS volume - 
```
/dev/sda6 /media/d_drives **vfat** users,gid=1000,uid=1000,fmask=0002,dmask=0002,defaults,rw,nosuid,flush 0 0
```


That is **not** NTFS.

---

### Post by kapiladhanvi on 2009-12-23
I went back and checked and the volume is indeed a FAT32 volume.  Sorry about the confusion. So the fstab entry is correct. 

I still dont know why I get this issue where the volume happens to load up as a read only volume instead of read-write. I would really appreciate any help I can get to resolve this. 

Thanks for taking a look at this issue. 

Dhanvi

PS: I went back and edited the subject and the message to correctly state the problem definition.

---

### Post by prince2689 on 2009-12-27
First instead of using all those commands, use a small but very useful software called pysdm.

You can get it through "sudo apt-get install pysdm".

And then you can use it through System->Administration->Storage Device Manager

It has all the options you need to mount any drive automatically at startup.......

It also has the rw or readonly option u need......

I personally advice u to use this software.........

---

