---
title: "Auto-mounting hard drive as user?"
date: 2009-08-24
forum: General Help
---

### Post by ankspo71 on 2009-08-24
Hi everyone,

I have been trying to automatically mount my storage hard drive as user instead of root, but I'm starting to think it can't be done. I searched this forum and I found a couple of lines to try in my fstab, 

/dev/hdb1 /media/disk vfat user,fmask=0111,dmask=0000 0   0 
This one didn't work at all for me, and the hard drive was reported as  missing. This problem happened with several configurations I found on the internet.

/dev/sdb1 /media/disk vfat defaults 0 1
This one worked for me, but it was mounted exclusively for root.

/dev/sdb1 /media/sdb1 vfat owner,users,user 0  0 
This one works the same as above (as root) but it will easily let me unmount and remount the drive as a user. I got this line by using a package called pysdm (storage device manager).

I also tried 
```
sudo chmod 777 /(mountpoint)
sudo mount -a (with and without mountpoint)
``` 
but it didn't help.

I had a big mishap when I accidentally moved a large amount of files and directories into a root only drive without being root. It took me a long time to get those permissions back in order, so I would like to avoid any more accidents like that. 

The main reason for auto-mounting is a so a large collection of music files doesn't have to keep getting reloaded in my music player. The reason I need full privileges is because I work with alot of the files, rearranging, editing, etc. I'm aware I can work from root by typing ```
 sudo nautilus /home
``` but then I still have files with root permissions.
Any ideas?
Thanks.

---

### Post by michy99 on 2009-08-24
Make sure that you are the owner of the mountpoint```
sudo chown YOURUSERNAME /MOUNTPOINT
```and try this for fstab line:```
/dev/sdb1 /media/disk vfat utf8,umask=007,uid=1000 0 2
```

---

### Post by ankspo71 on 2009-08-24
Thanks michy99,

I have it working the way I want it now.... I think. I have the drive mounted automatically, but now under my username and my groupname, and all permissions have been applied to the files and folders too. THis will work out fine, because I'm the only user who actually needs to access the other drive.

I tried adding the line you recommended in the fstab file but it didn't work out. I rebooted after adding the line, then ran chown with the -R operator and I got this

```
james@ubuntu:~$ sudo chown james /media/disk -R
[sudo] password for james: 
chown: cannot access `/media/disk': No such file or directory
james@ubuntu:~$ 
```

What you said about making sure I was the owner is what made it work for me. I also added the sync options to see what happens :). So the fstab now reads...

```
/dev/sdb1  /media/disk  vfat  uid=james,sync,gid=james,dirsync  0  2
``` 

It looks like I have it working now. I think I made it harder on myself trying to make it work for all users.
thanks for the help.
James

---

