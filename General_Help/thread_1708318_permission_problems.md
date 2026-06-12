---
title: "permission problems"
date: 2011-03-16
forum: General Help
---

### Post by nikoseubert on 2011-03-16
Hey There, 

i am having some trouble...maybe someone could give me a hint..

I logged in via ssh to a computer and i can delete stuff that i should not be able to delete.
I figured if the owner is different and the group is not mine and iit is 744 i should not be able to delete it...so i tested with "file1"..and i dont see my mistake:

users are "itv-storage" and "admin" on pc.
[HTML]
itv-storage@pc:/RAID5/storage/test$ ls -la
total 12
drwxrwxrwx 3 admin   admin   4096 2011-03-16 19:28 .
drwxrwxrwx 9 admin   admin   4096 2011-03-16 18:37 ..
-rwxr--r-- 1      admin   admin      0 2011-03-16 19:28 file1
drwxrwxrwx 3 itv-storage itv-storage 4096 2011-03-16 18:46 folder1
itv-storage@pc:/RAID5/storage/test$ rm file1 
rm: remove write-protected regular empty file `file1'? y
itv-storage@pc:/RAID5/storage/test$ ls -la
total 12
drwxrwxrwx 3 admin   admin   4096 2011-03-16 19:32 .
drwxrwxrwx 9 admin   admin   4096 2011-03-16 18:37 ..
drwxrwxrwx 3 itv-storage itv-storage 4096 2011-03-16 18:46 folder1
itv-storage@pc:/RAID5/storage/test$
[/HTML]what am i missing here?

thx!

---

### Post by Vi3tHoneyX on 2011-03-16
Welcome to the Forums! :D

[This page]("http://www.pageresource.com/cgirec/chmod.htm") should help out. It looks like you just have the permissions set to high. 

Gonna take a stab and say you are probably wanting 650 for your permissions. :)

---

### Post by sisco311 on 2011-03-16
You can delete the file because you have write permission on the directoy and execute on the directory, the directory's parent, and all ancestor directories up to and including "/" (the root directory). ;)

If you set the sticky bit on the directory, only the owner of a file or the owner of the directory (and the super-user of course) will be able to delete that file.
 
See:
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by SeijiSensei on 2011-03-16
First, what kind of filesystem is it?  ext3/4, NTFS, FAT32?  Windows filesystems don't have a Linux-compatible notion of permissions, so mounting them with the correct permissions can be tricky.  I'd read [this posting](http://ubuntuforums.org/showthread.php?t=1604251) if you're using one of those filesystem on the RAID device.

If you're using ext3 or ext4, then here's a procedure to fix the permissions on the entire filesystem.  I don't know whether the storage device is mounted at /RAID5 or at /RAID5/storage.  I'm guessing the latter.  If so, you want to turn off **g**roup and **o**ther write permissions for the entire filesystem like this:

```

cd /RAID5
chmod go-w storage -R

```

The "-R" switch tells chmod to "recurse" down the directory tree and change the permissions on everything it finds in /RAID5/storage and any subdirectories.  (If the device mounts at /RAID5, then you'd use "cd /; chmod go-w RAID5 -R" instead.)

Another possibility is that you made some custom re-configuration so that the "admin" user is really the "root" user, the one with uid=0.  If so, the user with ID zero can do anything anywhere.

---

### Post by nikoseubert on 2011-03-18
Hey Guys, 

thanks for the many answers!!
I think it is related to the sticky bit. I played arround a bit  and when i give the parent folder eg 1755 i can still read the files in that folder (not being the owner or belonging to a group) and not delete it..thats good...
but i can not create files in that folder either...

so is there a way that i can have the folder 777 and the files in there 755.. so that a person (not being the owner or belonging to a group) can read everything in there, but not delete it AND is able to create new stuff in that folder (due to 777)??


THX again!

---

### Post by r.osmanov on 2011-03-18
> **nikoseubert said:**
> so is there a way that i can have the folder 777 and the files in there 755.. so that a person (not being the owner or belonging to a group) can read everything in there, but not delete it AND is able to create new stuff in that folder (due to 777)??

What about just 1777?

---

