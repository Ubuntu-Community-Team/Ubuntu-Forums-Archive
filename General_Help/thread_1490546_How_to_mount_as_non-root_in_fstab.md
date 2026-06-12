---
title: "How to mount as non-root in fstab?"
date: 2010-05-22
forum: General Help
---

### Post by ChazZeromus on 2010-05-22
I'm really tired of having to umount under root, then mount again as a user for my external hard disk. When I'm in firefox, I like to save pages alot onto my external but I constantly have to remount because my user has no write permissions for the drive. **What can I do for my device in fstab so that it mounts automatically under my user and not root?**

---

### Post by jamesisin on 2010-05-22
You'll be better off changing permissions on the external drive.

---

### Post by ChazZeromus on 2010-05-22
I've done chown on the drive a lot of times but still mounts as root on startup.

---

### Post by akshay.sulakhe on 2010-05-22
use commands chmod -R 777 /dev/sda2
chown -R <username> /dev/sda2

use sudo before everything...and sda2 is an example...

---

### Post by ChazZeromus on 2010-05-22
I omitted the R option for this but it keeps saying:
```

root@ubuntu:~# chown chaz /media/MYBOOK -v
chown: changing ownership of `/media/MYBOOK': Operation not permitted
failed to change ownership of `/media/MYBOOK' to chaz

```


Since my device has the user option, maybe I need to add the option to make it non-auto then somehow make a script under my user to mount it?

---

### Post by jamesisin on 2010-05-22
What is the file system on this drive?

---

### Post by ChazZeromus on 2010-05-22
Ordinary FAT. I can understand why using FAT is not letting me change permissions in that way.

---

### Post by jamesisin on 2010-05-22
FAT doesn't have permissions.  Make sure the mount point you specified is owned by you (ie /media/MountPoint).

---

### Post by ChazZeromus on 2010-05-22
I've tried owning the directory after umounting, but it just goes back to root-owned after mounting again.
EDIT: I meant it goes back to root-owned after startup.

---

### Post by jamesisin on 2010-05-22
What is the line in fstab?

---

### Post by ChazZeromus on 2010-05-22
```

UUID=E1B5-218A	/media/MYBOOK	vfat	defaults,user	0	1

```
Also, upon checking the permissions, after remount the mount point was under my user but the files were still under root. Now it seems the mount-point completely went back to root. sigh, I'm so tired :D

---

### Post by jamesisin on 2010-05-22
With the drive mounted:

```
sudo chown [username]:[usergroup] /media/MYBOOK
sudo chmod 777 /media/MYBOOK
```

Please post the output.

( [http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587) )
( [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) )

---

### Post by ChazZeromus on 2010-05-22
```

chaz@ubuntu:~$ sudo chown chaz:chaz /media/MYBOOK
chown: changing ownership of `/media/MYBOOK': Operation not permitted
chaz@ubuntu:~$ sudo chmod 777 /media/MYBOOK
chaz@ubuntu:~$ 

```
The permissions on the mount point are still the same, I'm sorry. I've tried different groups, still no go.

---

### Post by jamesisin on 2010-05-22
Why don't you have permissions to change ownership of the mount point?

---

### Post by ChazZeromus on 2010-05-22
> **jamesisin said:**
> Why don't you have permissions to change ownership of the mount point?

Well since both commands are sudo'd I don't see why it's not working.

---

### Post by jamesisin on 2010-05-22
Did you create the /media/MYBOOK folder as root (not sudo but actually as root)?

---

### Post by ChazZeromus on 2010-05-22
> **jamesisin said:**
> Did you create the /media/MYBOOK folder as root (not sudo but actually as root)?
I think I made it as root. I'm deleting it and making remaking the directory under my user.

I got a permission error so I owned /media and it successfully made the MYBOOK directory again. I performed chown on the directory and still no go.

---

### Post by jamesisin on 2010-05-22
Root should own /media and if you changed that you will want to change it back.  When you have a clean /media (and you have removed your old mount point) then:

```
sudo mkdir MYBOOK
```

This will create a directory called MYBOOK owned by root.  Then run my previous commands.

---

### Post by drs305 on 2010-05-22
FAT doesn't work the way linux does. The permissions are set at mounting. It doesn't really matter who owns the mountpoint prior to the mounting. Try an fstab entry such as:

> UUID=E1B5-218A	/media/MYBOOK	vfat	defaults,user,uid=1000,umask=027 0 0

This assumes you are user 1000 (If you aren't the original user, check with "id" in terminal)

Check this thread by bodhi.zazen for more information:
[How to Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by ChazZeromus on 2010-05-22
> **drs305 said:**
> FAT doesn't work the way linux does. The permissions are set at mounting. It doesn't really matter who owns the mountpoint prior to the mounting. Try an fstab entry such as:



This assumes you are user 1000 (If you aren't the original user, check with "id" in terminal)

Check this thread by bodhi.zazen for more information:
[How to Fstab]("http://ubuntuforums.org/showthread.php?&t=283131")
Thank you it works!! But I think I need to change the umask parameters because I'm unable to view the permissions for the drive and files in Nautilus have little locks on them.
EDIT: No actually, I don't think I need to view the permissions as I believe this isn't a problem. Am I right?

---

