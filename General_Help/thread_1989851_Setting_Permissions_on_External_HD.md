---
title: "Setting Permissions on External HD"
date: 2012-05-28
forum: General Help
---

### Post by SuperFreak on 2012-05-28
I set permissions on my external hard drive using gksudo nautilus and allowing the owner(david) and group(david) to read and write files. I started copying files and folders from my storage internal Hard drive (ext 4) to my external hard drive (also ext 4) and I am getting error messages saying that files and folders can not be copied as they are in read only directories (see screenshot). I had a look at one of the folders in question on my internal drive and they have read write permissions   for owner (me-david) and group (me). What am I doing wrong ?

---

### Post by linuxman94 on 2012-05-28
Does your drive have a write protect switch?  If so, make sure it isn't locked.

---

### Post by SuperFreak on 2012-05-28
Not aware of any such switch. I bought the external HD case separately from the hd

---

### Post by linuxman94 on 2012-05-28
Please post the output of this command so we can determine the mount point of your drive.

```
mount
```

---

### Post by SuperFreak on 2012-05-28
Here is output

```
david@david-desktop:~$ mount
/dev/sda3 on / type ext4 (rw,noatime,nodiratime,discard)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda4 on /home type ext4 (rw,noatime,nodiratime,discard)
/dev/sdb1 on /media/STORAGE type ext4 (rw,relatime,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/david/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=david)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)
/dev/sdc1 on /media/Storage 2 type ext4 (rw,nosuid,nodev,uhelper=udisks)
david@david-desktop:~$ 

```

The external drive is Storage 2 on last line

---

### Post by SuperFreak on 2012-05-29
Bump

I notice that ```
/dev/sdb1 on /media/STORAGE type ext4 (rw,relatime,errors=remount-ro)
```

shows remount-ro does this mean that it is remounted as read only? This is the drive I am transferring from (to Storage 2)

---

### Post by anonymous5 on 2012-05-29
> **SuperFreak said:**
> Bump

I notice that ```
/dev/sdb1 on /media/STORAGE type ext4 (rw,relatime,errors=remount-ro)
```

shows remount-ro does this mean that it is remounted as read only? This is the drive I am transferring from (to Storage 2)

You are copying files to Storage 2 ? Try this :

sudo chmod 777 -R /media/Storage 2

---

### Post by SuperFreak on 2012-05-29
@anonymous5  Thanks for your suggestion. I wasn't completely comfortable with giving everyone rights to that directory  so I changed the command to 
```
sudo chmod 770 -R /media/Storage\ 2 
```. 
Unfortunately I am still getting the same error messages

Further problems. I did intially copy some files before the error messages displayed and I terminated the copy process. I find now that none of the files are readable and I am not able to delete them even when using sudo privledges

---

### Post by linuxman94 on 2012-05-30
If you don't have anything you need to keep on the drive or you can make a copy of it, I would suggest reformatting the drive.

---

### Post by bab1 on 2012-05-30
> **linuxman94 said:**
> If you don't have anything you need to keep on the drive or you can make a copy of it, I would suggest reformatting the drive.

Without really good look at this thread I would say that the OP needs to set group ID (sgid)  on the directory he is going to use for this project.

I'm on the way out for a few hours but will return to this for a more detailed explanation.

---

### Post by SuperFreak on 2012-05-30
@linuxman94 - Reformatting was my next move as the drive is empty anyway, but I was hoping to find out why I am getting error messages

@bab1  - I am in no great hurry on this so I will wait awhile for a reply from you. My preference is to learn how to make the drive work properly without the error messages when I copy files. I know it might be more expedient to just reformat and start over but I am trying to become more comfortable setting permissions as you must know from answering another thread I started

I did google some of the error messages (one was concerning "splicing" a file copy) and discovered that Ubuntu has trouble copying encrypted Windows files (these were old dbx files from Outlook Express). Also there was an error copying sbd folders which I believe are Thunderbird folders. I am thinking that because Thunderbird was open at the time I was copying that might have been the problem (the Local Directory for my Thunderbird files was one of the directories I was copying).
I will try working my way through some of the Man pages and guides on the net regarding permissions; it is a little daunting still

---

### Post by bab1 on 2012-05-31
> **SuperFreak said:**
> I set permissions on my external hard drive using gksudo nautilus and allowing the owner(david) and group(david) to read and write files. 
I'll try to point out the reasons why things are as they are and  what to you can do to configure the file system to your liking.  Let's take your above thought and break it down.  The first thing you should know is that Debian developers made a conscious decision to configure the system with "private groups".  This means that the group has no members and nobody can use group access by default.  You have to configure public groups (i.e with members yourself).  For example if you look at the membership of the *group* david you will see there is no one in that group.  ```
getent group|grep david
david:x:1000:
```What we have is *the name of the [COLOR="Red"]group[/COLOR]:no pass:[COLOR="Blue"]gid[/COLOR]:  and no members.*

At first this seems wrong. But if you think about it, the group permissions don't add any functionality for the user david.  If he can access as the owner he doesn't need access via the group.
> 
I started copying files and folders from my storage internal Hard drive (ext 4) to my external hard drive (also ext 4) and I am getting error messages saying that files and folders can not be copied as they are in read only directories (see screenshot). I had a look at one of the folders in question on my internal drive and they have read write permissions   for owner (me-david) and group (me). What am I doing wrong ?

I believe we will see why in the next few lines.

You were asked to show all the partitions mounted.  You responded with```
/dev/sdc1 on /media/Storage 2 type ext4 (rw,nosuid,nodev,**[COLOR="Red"]uhelper=udisks[/COLOR]**)
```

At this point I would delete the part in red.  I don't believe it's appropriate in this context.> I wasn't completely comfortable with giving everyone rights to that directory so I changed the command to```
sudo chmod 770 -R /media/Storage\ 2

```
It would be wise to decide whether the files and folders on the partition "Storage 2" are going to be shared by other users.  If so then we need to configure that.

If you want to make the group membership meaningful, allowing you to share data with others, you need to set the sgid (set group ID) bit in the permissions on the root directory of the shared file system.  This is not the / directory of the entire system.  For example all of my samba shares are located below /smb.  If you wanted to use /media/smb you could do that.  Why do you want the mount point to be under /media?

It is tough to get your head around permission and now I throw additional permissions at you.  The permissions 770 are really 0770.  if we were to add the sgid we would have 2770.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for some detail on suid, sgid and the sticky bit permissions.  For more info on permissions in general see [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml").

To summarize;  [LIST]
[*]Try removing the **[COLOR="Red"]uhelper=udisks[/COLOR]** in the mount instuction and see if it then mounts as rw.
[*]If you want to use this system for shared data we need to set up group membership and sgid and ...
[*] Set the appropriate permissions for the directories (2775) and files (0664) 

If you are interested we can set up a simple test file structure in your home directory and configure that first.  I just did exactly that for a friend yesterday.  It worked perfectly and is a good learning tool. 
[/LIST]

[COLOR="Blue"]Edit: Some of this will help you with your post from 3 weeks ago regarding symlinks and permissions.[/COLOR]

---

### Post by SuperFreak on 2012-05-31
Ok Bab1

Do I remove uhelper=udisks in fstab?

---

### Post by Morbius1 on 2012-05-31
Some random observations:

[COLOR=Blue]**EDIT**[/COLOR]: Just saw your last post:
> Do I remove uhelper=udisks in fstab?     Only if you set up an entry for /media/Storage 2 in fstab. If you did then post contents of the whole thing:
```
cat /etc/fstab
```This is an external USB drive formatted in ext4 right?
> /dev/sdc1 on /media/Storage 2 type ext4 (rw,nosuid,nodev,uhelper=udisks)If you did not have an entry in fstab for this device then this output from "mount" is normal and the way it should be mounting so there's no way ( without messing about with internal system defaults ) and no need to remove "uhelper=udisks" from anything. 

What seems to be missing here is a description of the ownership and permissions of the "copy from" and "copy to" destinations. What are the permissions on the external device:
```
ls -al "/media/Storage 2"
```> **SuperFreak said:**
> I notice that ```
/dev/sdb1 on  /media/STORAGE type ext4 (rw,relatime,errors=remount-ro)
```shows  remount-ro does this mean that it is remounted as read only? This is the  drive I am transferring from (to Storage 2)
"errors=remount-ro" means that during boot, when the system does a file system check, if it finds a problem with the partition instead of not mounting it at all it will mount it as "read only".  This may or may not have happened in your case but it could be one of the things that are wrong in this situation. Are you having any issues with writing to /media/STORAGE? Bases on the mount output of /media/STORAGE it appears to be mounting rw so this might not be an issue but ...

> I did initially copy some files before the error messages displayed and I terminated the copy process. I find now that none of the files are readable and I am not able to delete them even when using sudo privledges     Not sure why even root cannot delete the files but since you terminated ( btw - how did you terminate it ) the copy process you don't know what state those files are in.

---

### Post by SuperFreak on 2012-05-31
I hope I am not creating confusion here but out of frustration and a suggestion by one of the posters I reformatted the drive. To answer your question Morbius1 the output of ls -al is:

```
david@david-desktop:~$ ls -al "/media/Storage2"
ls: cannot access /media/Storage2: No such file or directory
david@david-desktop:~$ ls -alls -al "/media/Storage2"
total 24
 4 drwxr-xr-x 3 root root  4096 May 30 21:31 .
 4 drwxr-xr-x 4 root root  4096 May 31 08:07 ..
16 drwx------ 2 root root 16384 May 30 21:31 lost+found
david@david-desktop:~$ 


```

I never did set any entries in fstab for the drive

I terminated the copy process by clicking on the file close button in the operation window. I realize this probly caused problems now

I have just been reading the link page you referred me to bab1 about sgid and while I haven't quite grasped that concept the general information about file permissions notation has been very informative.

---

### Post by Morbius1 on 2012-05-31
Well, since you reformatted the drive all you need to do is take possession of the mounted partition:
```
sudo chown david:david /media/Storage2
```[COLOR=Blue]*Oh, and thank you for removing the space between Storage and 2 :)*[/COLOR]

If you have multiple users on that box then you can change groups and permissions and use setgid and all that but if you are the only user then changing ownership to you is all you need to do.

---

### Post by SuperFreak on 2012-05-31
@Morbius1
```
sudo chown david:david /media/Storage2
```
worked. Thank you for your help.

I think I have some reading to do to understand more about permissions and sgid/suid. I appreciate the help everyone has given me

---

