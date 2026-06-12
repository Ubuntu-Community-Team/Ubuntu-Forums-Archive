---
title: "USB flash drive - permissions problem"
date: 2009-08-26
forum: General Help
---

### Post by RuleMaker on 2009-08-26
I understand the permissions very well and I have a good knowledge of using chmod, chown, chgrp commands...all works fine on my hard drive...
Recently I took the usb flash drive to my friend who uses windows OS and put some pictures on it, the problem is that I cant copy or even view the pictures or even change their permissions (like they are read only).

Please take a look at the following:
```
rulemaker@linux ~ $ ls -l /media/sdb1/slike/
total 35224
-rwx**rwx**rwx 1 root **rulemaker** 1244349 2007-01-05 18:52 IMG_0001.jpg
-rwxrwxrwx 1 root rulemaker 1378807 2007-01-05 18:53 IMG_0002.jpg
-rwxrwxrwx 1 root rulemaker 1413116 2007-01-05 18:58 IMG_0008.jpg
-rwxrwxrwx 1 root rulemaker 1999790 2007-01-07 10:36 IMG_0039.jpg
-rwxrwxrwx 1 root rulemaker 1378379 2007-08-02 18:35 IMG_0676.jpg
-rwxrwxrwx 1 root rulemaker 1294775 2007-08-20 13:59 IMG_0725.jpg
-rwxrwxrwx 1 root rulemaker 1108916 2007-08-20 14:00 IMG_0726.jpg
-rwxrwxrwx 1 root rulemaker 1211343 2007-08-22 13:27 IMG_0740.jpg
-rwxrwxrwx 1 root rulemaker 7120580 2009-08-25 17:31 MVI_2930.avi
-rwxrwxrwx 1 root rulemaker 5495032 2009-08-25 17:32 MVI_2931.avi
-rwxrwxrwx 1 root rulemaker 1746264 2009-08-25 17:42 STA_2939.jpg
-rwxrwxrwx 1 root rulemaker 1597301 2009-08-25 17:43 STB_2940.jpg
-rwxrwxrwx 1 root rulemaker 1221637 2009-08-25 17:43 STC_2941.jpg
-rwxrwxrwx 1 root rulemaker 1311036 2009-08-25 17:33 STD_2935.jpg
-rwxrwxrwx 1 root rulemaker 1656766 2009-08-25 17:44 STD_2942.jpg
-rwxrwxrwx 1 root rulemaker 1526508 2009-08-25 17:44 STE_2943.jpg
-rwxrwxrwx 1 root rulemaker 1518143 2009-08-25 17:44 STF_2944.jpg
-rwxrwxrwx 1 root rulemaker 1812676 2009-08-25 17:44 STG_2945.jpg
```

```
rulemaker@linux ~ $ groups rulemaker 
**rulemaker** adm dialout cdrom audio plugdev scanner fuse lpadmin admin sambashare
```

As you can see I am in the rulemaker group, shouldn't I have rwx permissions on all files?

moreover...I tried using chown to change the user to my user, but it haven't changed and didnt print out any error.

```
rulemaker@linux ~ $ sudo chown -R rulemaker:rulemaker /media/sdb1/slike
[sudo] password for rulemaker: 
rulemaker@linux ~ $ ls -l /media/sdb1/slike/
total 35224
-rwxrwxrwx 1 root rulemaker 1244349 2007-01-05 18:52 IMG_0001.jpg
-rwxrwxrwx 1 root rulemaker 1378807 2007-01-05 18:53 IMG_0002.jpg
-rwxrwxrwx 1 root rulemaker 1413116 2007-01-05 18:58 IMG_0008.jpg
-rwxrwxrwx 1 root rulemaker 1999790 2007-01-07 10:36 IMG_0039.jpg
-rwxrwxrwx 1 root rulemaker 1378379 2007-08-02 18:35 IMG_0676.jpg
-rwxrwxrwx 1 root rulemaker 1294775 2007-08-20 13:59 IMG_0725.jpg
-rwxrwxrwx 1 root rulemaker 1108916 2007-08-20 14:00 IMG_0726.jpg
-rwxrwxrwx 1 root rulemaker 1211343 2007-08-22 13:27 IMG_0740.jpg
-rwxrwxrwx 1 root rulemaker 7120580 2009-08-25 17:31 MVI_2930.avi
-rwxrwxrwx 1 root rulemaker 5495032 2009-08-25 17:32 MVI_2931.avi
-rwxrwxrwx 1 root rulemaker 1746264 2009-08-25 17:42 STA_2939.jpg
-rwxrwxrwx 1 root rulemaker 1597301 2009-08-25 17:43 STB_2940.jpg
-rwxrwxrwx 1 root rulemaker 1221637 2009-08-25 17:43 STC_2941.jpg
-rwxrwxrwx 1 root rulemaker 1311036 2009-08-25 17:33 STD_2935.jpg
-rwxrwxrwx 1 root rulemaker 1656766 2009-08-25 17:44 STD_2942.jpg
-rwxrwxrwx 1 root rulemaker 1526508 2009-08-25 17:44 STE_2943.jpg
-rwxrwxrwx 1 root rulemaker 1518143 2009-08-25 17:44 STF_2944.jpg
-rwxrwxrwx 1 root rulemaker 1812676 2009-08-25 17:44 STG_2945.jpg
```

As you can see the owner is still root, am I doing something wrong?

Here is the line from blkid:
```
/dev/sdb1: UUID="0FB62F750C820D0F" LABEL="USB" TYPE="ntfs"
```
(maybe I have to change something in my fstab?)

Thanks in advance and sorry for a long post, I just tried to supply with as much info as possible.

---

### Post by cdenley on 2009-08-26
NTFS filesystems do not support linux file permissions. They are assigned at mount time.
```

sudo umount /media/sdb1
sudo mount -t ntfs-3g -o fmask=177,dmask=077,uid=$UID /dev/sdb1 /media/sdb1
cp -v /media/sdb1/slike/IMG_0001.jpg ~

```

Your access to filesystems is determined by your group membership when logged in. Have you added yourself to the "rulemaker" group recently?
```

id

```

---

### Post by RuleMaker on 2009-08-26
```
rulemaker@linux /media $ id
uid=1000(rulemaker) gid=1000(rulemaker) groups=4(adm),20(dialout),24(cdrom),29(audio),46(plugdev),104(scanner),106(fuse),112(lpadmin),120(admin),122(sambashare),1000(rulemaker)
```

Thanks for your reply, now the situation is a bit different but the result is the same - permission denied
```
rulemaker@linux /media $ cp disk/slike/* ~
cp: cannot open `disk/slike/IMG_0001.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0002.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0008.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0039.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0676.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0725.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0726.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0740.jpg' for reading: Permission denied
cp: cannot open `disk/slike/MVI_2930.avi' for reading: Permission denied
cp: cannot open `disk/slike/MVI_2931.avi' for reading: Permission denied
cp: cannot open `disk/slike/STA_2939.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STB_2940.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STC_2941.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STD_2935.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STD_2942.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STE_2943.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STF_2944.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STG_2945.jpg' for reading: Permission denied
rulemaker@linux /media $ ls -l disk/slike/
total 35224
-rw------- 1 rulemaker root 1244349 2007-01-05 18:52 IMG_0001.jpg
-rw------- 1 rulemaker root 1378807 2007-01-05 18:53 IMG_0002.jpg
-rw------- 1 rulemaker root 1413116 2007-01-05 18:58 IMG_0008.jpg
-rw------- 1 rulemaker root 1999790 2007-01-07 10:36 IMG_0039.jpg
-rw------- 1 rulemaker root 1378379 2007-08-02 18:35 IMG_0676.jpg
-rw------- 1 rulemaker root 1294775 2007-08-20 13:59 IMG_0725.jpg
-rw------- 1 rulemaker root 1108916 2007-08-20 14:00 IMG_0726.jpg
-rw------- 1 rulemaker root 1211343 2007-08-22 13:27 IMG_0740.jpg
-rw------- 1 rulemaker root 7120580 2009-08-25 17:31 MVI_2930.avi
-rw------- 1 rulemaker root 5495032 2009-08-25 17:32 MVI_2931.avi
-rw------- 1 rulemaker root 1746264 2009-08-25 17:42 STA_2939.jpg
-rw------- 1 rulemaker root 1597301 2009-08-25 17:43 STB_2940.jpg
-rw------- 1 rulemaker root 1221637 2009-08-25 17:43 STC_2941.jpg
-rw------- 1 rulemaker root 1311036 2009-08-25 17:33 STD_2935.jpg
-rw------- 1 rulemaker root 1656766 2009-08-25 17:44 STD_2942.jpg
-rw------- 1 rulemaker root 1526508 2009-08-25 17:44 STE_2943.jpg
-rw------- 1 rulemaker root 1518143 2009-08-25 17:44 STF_2944.jpg
-rw------- 1 rulemaker root 1812676 2009-08-25 17:44 STG_2945.jpg
```

Now I am the owner and have rw permissions and still can't copy them, how come?

EDIT:
Could you explain me the fmask and dmask?

---

### Post by cdenley on 2009-08-26
> **RuleMaker said:**
> 
Could you explain me the fmask and dmask?

fmask=177 means set file permissions to 600
dmask=077 means set directory permissions to 700
uid=$UID means set the owner UID to the value of $UID, which is the UID of your current user
```

man ntfs-3g

```

I'm not sure why you're having problems. You appear to have the correct permissions.

---

### Post by RuleMaker on 2009-08-26
Thanks for explanation.

This is so strange, now i tried to mount it with the following command:
```
sudo mount -t ntfs-3g -o fmask=000,dmask=000,uid=1000,gid=1000 /dev/sdc1 /media/disk
```
And it gave all possible permissions and I'm still getting the permission denied message.
```

rulemaker@linux /media $ ls -l /media/disk/slike/
total 35224
-rwxrwxrwx 1 rulemaker rulemaker 1244349 2007-01-05 18:52 IMG_0001.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1378807 2007-01-05 18:53 IMG_0002.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1413116 2007-01-05 18:58 IMG_0008.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1999790 2007-01-07 10:36 IMG_0039.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1378379 2007-08-02 18:35 IMG_0676.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1294775 2007-08-20 13:59 IMG_0725.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1108916 2007-08-20 14:00 IMG_0726.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1211343 2007-08-22 13:27 IMG_0740.jpg
-rwxrwxrwx 1 rulemaker rulemaker 7120580 2009-08-25 17:31 MVI_2930.avi
-rwxrwxrwx 1 rulemaker rulemaker 5495032 2009-08-25 17:32 MVI_2931.avi
-rwxrwxrwx 1 rulemaker rulemaker 1746264 2009-08-25 17:42 STA_2939.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1597301 2009-08-25 17:43 STB_2940.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1221637 2009-08-25 17:43 STC_2941.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1311036 2009-08-25 17:33 STD_2935.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1656766 2009-08-25 17:44 STD_2942.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1526508 2009-08-25 17:44 STE_2943.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1518143 2009-08-25 17:44 STF_2944.jpg
-rwxrwxrwx 1 rulemaker rulemaker 1812676 2009-08-25 17:44 STG_2945.jpg
rulemaker@linux /media $ cp disk/slike/* ~
cp: cannot open `disk/slike/IMG_0001.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0002.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0008.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0039.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0676.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0725.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0726.jpg' for reading: Permission denied
cp: cannot open `disk/slike/IMG_0740.jpg' for reading: Permission denied
cp: cannot open `disk/slike/MVI_2930.avi' for reading: Permission denied
cp: cannot open `disk/slike/MVI_2931.avi' for reading: Permission denied
cp: cannot open `disk/slike/STA_2939.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STB_2940.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STC_2941.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STD_2935.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STD_2942.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STE_2943.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STF_2944.jpg' for reading: Permission denied
cp: cannot open `disk/slike/STG_2945.jpg' for reading: Permission denied

```

I haven't mentioned that the USB drive got a bit buggy and it suddenly became sdc instad of sdb which it should be since it's the only memory attached to my PC next to my hard drive.

Any ideas?

---

### Post by cdenley on 2009-08-26
If the drive was disconnected while it was mounted, then I think it would become sdc. You can try the ntfscat command while it is unmounted.
```

sudo apt-get install ntfsprogs
sudo ntfscat /dev/sdc1 /slike/IMG_0001.jpg > IMG_0001.jpg
ls -l IMG_0001.jpg

```

---

### Post by RuleMaker on 2009-08-26
Hmm, this is the result of executing the ntfscat:
```
Access is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
You can use force option to avoid this check, but this is not recommended
and may lead to data corruption.
ERROR: couldn't mount volume: No such file or directory.
```

---

### Post by cdenley on 2009-08-26
Your computer seems to think the filesystem is already mounted somewhere else. Did you unmount it before running that command? What is the output of this command?
```

grep ^/dev/sd /etc/mtab

```
Can you try rebooting?

---

### Post by RuleMaker on 2009-08-26
I've already tried rebooting, this is the output after reboot:
```
rulemaker@linux ~ $ grep ^/dev/sd /etc/mtab
/dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
/dev/sda6 /home ext3 rw,relatime 0 0
/dev/sdb1 /media/disk fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
```

---

### Post by cdenley on 2009-08-26
/dev/sdb1 needs to be unmounted before running the ntfscat command.

---

### Post by RuleMaker on 2009-08-26
I don't get it, it is the USB flash drive, if I unmount it the rest of command wont make sense.

---

### Post by cdenley on 2009-08-26
ntfscat reads files directly from an ntfs filesystems which are not mounted. The error you posted before indicated you were running ntfscat to read a file from an ntfs filesystem which was already mounted, which is incorrect.

---

### Post by RuleMaker on 2009-08-26
```
rulemaker@linux /media $ sudo ntfscat /dev/sdb1 /slike/IMG_0001.jpg > IMG_0001.jpg
bash: IMG_0001.jpg: Permission denied
```

---

### Post by cdenley on 2009-08-27
It must be encrypted. I just tested it, and you receive "Permission denied" when attempting to read an encrypted file on an NTFS filesystem. You can only read encrypted files on the Windows computer which had encrypted it, as far as I know.

---

### Post by RuleMaker on 2009-08-27
> **cdenley said:**
> It must be encrypted. I just tested it, and you receive "Permission denied" when attempting to read an encrypted file on an NTFS filesystem. You can only read encrypted files on the Windows computer which had encrypted it, as far as I know.
I'd never think about that!
Thanks man, that was a problem.

---

