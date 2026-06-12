---
title: "Change Folder Permission (chown doesn't work )"
date: 2009-08-10
forum: General Help
---

### Post by sonnet on 2009-08-10
I'm trying to change permission to all the folder included in the /media/ folder (which includes different partitions ).
All the folder under this directory are owned by the root
I used the command chown under my account (with sudo) and I tried with the root account/It seemed to get it but if I look at the permission tab the folders are still owned by the root.
I tried launching directly nautilus with sudo but when I try to change permission (which is selectable) after I select my account it autoreselect the root.
Everytime I tried any changes I restarted the pc to see if then it could get the changes.
I'm using Jaunty 64 bit.
Any idea what could I do?

---

### Post by merlinus on 2009-08-10
Exactly what commands did you try?  Since /media is a system directory, it needs to be owned by root, but you can change ownership/permissions on the folders within it recursively.

An alternative is to mount those folders in a different directory, one which you create, such as /shared, or /data.  Then you could own the mountpoint as well.

---

### Post by sonnet on 2009-08-10
> **merlinus said:**
> Exactly what commands did you try?  Since /media is a system directory, it needs to be owned by root, but you can change ownership/permissions on the folders within it recursively.

An alternative is to mount those folders in a different directory, one which you create, such as /shared, or /data.  Then you could own the mountpoint as well.

the command I tried was:
sudo chown myusername:myusername /media 
or
sudo chown myusername:myusername /media/
or
sudo chown myusername:myusername /media/Data
or
sudo chown myusername:myusername /media/Data/

So as you see above I tried even with the folder inside /media/
but it didn't work.
Forgive my ignorance but which command should I use to apply the alternative you suggested?

---

### Post by michy99 on 2009-08-10
What type of filesystem is on Data? If it is FAT32 or NTFS, the permissions are set when the partition is mounted.

---

### Post by bacardiandwatermelon on 2009-08-10
Is it an external drive?

---

### Post by sonnet on 2009-08-10
> **michy99 said:**
> what type of filesystem is on data? If it is fat32 or ntfs, the permissions are set when the partition is mounted.

ntfs
and are all internal drives

---

### Post by michy99 on 2009-08-10
Check out this page for a good way to deal with NTFS drives:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by sonnet on 2009-08-10
> **michy99 said:**
> Check out this page for a good way to deal with NTFS drives:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

Thanks guys for all the reply.
Unfortunately the problem is still there.
I tried the application suggested in the guide you posted, and it looked very easy to use. Apparently it also give me the permission to the partition and all the subfolder within it.
The tricky thing is that even if I am now the owner of the partition and the folder included , I cannot delete any folder,file neither create or move anything within the partition.
How is that possible?
I'm sure I didn't have this issues with Hardy.Why?

---

### Post by dolomit on 2010-09-02
hi

im using ubuntu 10.04 and had the same problem. After a while of utilization i had 2 empty folders in my media folder which ive removed with sudo nautilus in terminal and deleting the folders with nautilus right mouse menu.

i have a partition automounter "pysdm" and this was the program that created them, after i disable the automount function it dos not delete the folder in media folder.

hope it helps.

---

