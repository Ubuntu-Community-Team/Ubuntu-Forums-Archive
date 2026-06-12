---
title: "chown on external disk: messed up file ownership"
date: 2011-04-18
forum: General Help
---

### Post by sam81 on 2011-04-18
I have an external drive formatted as ext3 that I mount through fstab

everything was working well until I decided to give a shot to PC-BSD: it would mount my disk but I could not write on it, so I did a chown -R user:user /path/to_disk and got my write access from BSD, I can't remember whether "user" was my username or it was "root". 

But then I lost write permissions on ubuntu, so I did chown -R root:root /path/to_disk, now I have write permission on ubuntu, but there is some inconsistencies, the directories appear all owned by root, but if I create a new file or directory, then it is owned by me. So far so good, but if I login as another user, then I don't have write access to the directories/files created by me...

unfortunately I don't remember what were the original file permission settings...

how can I bring the situation back to normal?

---

### Post by Morbius1 on 2011-04-18
>  how can I bring the situation back to normal?     There is no normal. Files and folders in a Linux filsystem contain the ownership and permissions within them so without knowing what it was in the beginning there is no bringing it back.

Post the output of the following command so others can see where you are now:
```
ls -al /path/to_disk
```

---

### Post by Leppie on 2011-04-18
it may also be helpful to post your fstab, to see what parameters are used to mount the drive.

---

### Post by sam81 on 2011-04-18
Thanks for the help!

I see, there is no normal if I don't know what was the original state, I know how originally got all my data on that ext3 disk when it was freshly formatted, I copied them over as a normal user (probably with grsync) from an NTFS drive (which as far as I know does not have file permissions per se). Maybe I will copy everything to the NTFS drive, re-format the ext3 drive and copy things back to get back to where I was...

this is the output of ls -al /path/to_disk (filenames removed for privacy):

drwxrwxrwx 19 root root     4096 2011-04-18 21:03 .
drwxr-xr-x  4 root root     4096 2011-04-18 21:57 ..
drwxrwxrwx  2 root root     4096 2011-04-16 02:04 
drwxrwxrwx  2 root root     4096 2011-04-15 22:50 
drwxrwxrwx  2 root root     4096 2011-01-18 19:29 
drwxrwxrwx  2 root root     4096 2011-03-31 19:37 
drwxrwxrwx  2 root root     4096 2010-12-22 16:31 
-rwxrwxrwx  1 root root    21504 2011-04-06 14:23 
-rwxrwxrwx  1 root root       39 2010-12-08 14:24 
drwxrwxrwx  2 root root     4096 2011-03-13 13:40 
-rwxrwxrwx  1 root root   743645 2011-02-24 14:55 
-rwxrwxrwx  1 root root       62 2011-03-14 03:07 
-rw-r--r--  1 root root        2 2011-03-13 20:55 
-rwxrwxrwx  1 root root    10009 2011-03-28 10:51 
drwxrwxrwx 18 root root     4096 2011-04-18 21:33 
drwxrwxrwx  2 root root    16384 2010-03-23 12:46 
drwxrwxrwx  2 root root     4096 2011-03-06 18:14 
drwxrwxrwx 10 root root     4096 2011-04-18 21:54 
-rwxrwxrwx  1 root root      898 2011-04-14 10:32 
drwxrwxrwx 20 root root     4096 2011-03-04 12:33 
drwxrwxrwx  2 root root     4096 2011-04-06 20:54 
-rwxrwxrwx  1 root root   172544 2010-11-25 20:06 
-rwxrwxrwx  1 root root   199317 2010-11-25 17:05 
drwxrwxrwx  2 root root     4096 2011-03-13 13:44 
drwxrwxrwx  2 root root     4096 2010-12-06 19:45 
-rwxrwxrwx  1 root root   139142 2011-03-17 13:21 
-rw-r--r--  1 root root 13672465 2011-04-17 01:53 
-rwxrwxrwx  1 root root  7371894 2011-03-30 17:46 
drwxrwxrwx 10 root root     4096 2011-01-15 22:47 
drwxrwxrwx  4 root root     4096 2011-04-15 18:23 .Trash-1000
drwx------  4 root root     4096 2011-04-18 21:04 .Trash-1001

---

### Post by sam81 on 2011-04-18
this is the fstab line that I use to mount the drive:

LABEL=exodisk /media/ntfsShared ext3 defaults,rw,users,exec,user_xattr 0 0

forgot to mention, I also did chmod -R 777 /media/path_to_disk

---

### Post by Morbius1 on 2011-04-18
I read your original post again and the things you posted so far and I think you are going to have a problem trying to do what I think you want to do.

With /path/to_disk as root:root 777 every one will be able to add to or delete from that partition. But when user1 adds a file it will save as user1:user1 644. User1 can read and write but everyone else can only read. This is the way it works by default.

You can fix that for all the local login users. For example you can set the group to plugdev ( all local ubuntu users are members of plugdev by default ), set the permissions to 2775 ( this will force every new file to "inherit" the group of the parent folder ), and change the default umask to 002 in /etc/profile. Then every new file saved by user1 will save as user1: plugdev 664. User1 and all members of the plugdev group will now be able to write to the file.

But this is an external drive so you will have to change the umask default and perhaps create a plugdev group ( with the same gid number ) on every box that this drive comes in contact with. Even is this was a dual boot with another linux-like OS you would have to replicate that procedure. Linux filesystems on removable drives just don't work as smoothly as one formatted in NTFS or Fat32.

---

### Post by sam81 on 2011-04-18
many thanks for the help and the explanation, I'm going to try and start with a clean slate by formatting the ext3 drive and recopying all files from my NTFS backup drive, this should bring things back as they were before

I'm not sure this will solve the problem if different users want to write and modify the same files, I have the same username on almost every machine were I use the disk, so I haven't tested this throughly

at the moment I have odd things happening, like grsync doesn't want to copy new files that I've added since I messed things up on the ext3 driver over to the NTFS drive...unless I do it as root

---

### Post by Morbius1 on 2011-04-18
> **sam81 said:**
> I'm not sure this will solve the problem if different users want to write and modify the same files, I have the same username on almost every machine were I use the disk, so I haven't tested this throughly

If you have the same username and the the OS's are all Ubuntu or Debian based then you might be OK. But if the other OS is say a Red Hat derivative ( i.e., Fedora, Mandriva, PCLinuxOS ) then you will have a problem. User1 on Ubuntu has a uid of 1000. User1 on say PCLinuxOS is 500. So User1 does not equal User1. You can change the uid of the user on the other machine but things are getting way complicated here.

---

### Post by sam81 on 2011-04-18
I see... probably that's why also I had trouble getting write permission in PC-BSD although the username was the same. I'm going to re-format the disk to NTFS, any suggestion on how to mount it with fstab?

---

### Post by Leppie on 2011-04-18
if you want a quick way, install ntfs-config:
```
sudo apt-get install ntfs-config
```

answer a couple  of questions after the installation and you're good to go

---

### Post by sam81 on 2011-04-18
thanks, I'll try that, I'm formatting to NTFS right now

---

### Post by Morbius1 on 2011-04-19
> **sam81 said:**
> I'm going to re-format the disk to NTFS, any suggestion on how to mount it with fstab?
Yes, Don't mount it in fstab. An external ntfs or fat32 formatted external usb device will automatically mount when plugged in with the current user as owner with full read / write access to that user. It will by design mount to /media/LABEL - where LABEL is the label on the partition itself or if it can't find one to /media/UUID-number. I don't know if BSD does the same.

---

