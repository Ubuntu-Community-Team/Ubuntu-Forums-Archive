---
title: "Making the file executable"
date: 2012-03-07
forum: General Help
---

### Post by livin4th on 2012-03-07
Hi,
        My introductory programming course requires me to do a lot of compiling and executing the compiled code. However being new to programming in linux, it took me a while to figure out that the reason my compiled code returns  "permission denied" when I try to execute my executable is something to do with permissions of the directory. I know 

>  
chmod a+x filename

changes the permission of a file to  make it executable. The command gets executed without any error but still the file doesn't get the executable permission. when I do ls -al the permission is still read only.

Can anyone please tell me if I am missing something.

thanks,
Livin

---

### Post by jerome1232 on 2012-03-07
What file-system are you storing the executables on? 

I ask because...

MS file-systems have linux style permissions assigned to the entire volume at mount time and cannot be changed via chmod or chown, but must be set with the correct mount options.

---

### Post by livin4th on 2012-03-07
Not quite sure.. how do I know which FS I am using? is there a command to find it out?

---

### Post by ofnuts on 2012-03-07
> **livin4th said:**
> Not quite sure.. how do I know which FS I am using? is there a command to find it out?
"mount" (without args) will tell you all the filesystems and their type.

---

### Post by Cavsfan on 2012-03-07
```
sudo chmod +x file name location
eg. sudo chmod +x /etc/grub.d/10_linux  
```

makes it executable

```
sudo chmod -x file name location
eg. chmod -x /etc/grub.d/10_linux
```

makes it unexecutable.

---

### Post by livin4th on 2012-03-07
Thanks. I ran that and it turns out it uses a FS of type fuseblk..heres the exact line of output

> 
/dev/sda6 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


---

### Post by jerome1232 on 2012-03-07
it's probably actually fat or ntfs (fuseblk isn't actually a filesystem)

A temporary way to get execute permission on it would be to unmount it, then remount it with these options ( i think )

```
sudo umount /dev/sda6
sudo mkdir /media/temp
sudo mount /dev/sda6 /media/temp -o umask=000
```

When your done

```
sudo umount /dev/sda6
sudo rmdir /media/temp
```

---

### Post by livin4th on 2012-03-07
wow..that worked..so we basically mount the partition somewhere else and that changes its file system?

is it ok to leave it mounted or do we have to unmount it without fail?

and thanks for ur help.

---

### Post by jerome1232 on 2012-03-07
Well no, you can mount it anywhere you want, it's the -o umask=000 that changed permissions (umask=000 means read,write, and execute for all users, you can adjust that as you please)


Is this a USB disk or an internal disk?

edit: It's okay to leave it mounted, if it's a usb disk you need to unmount it before disconnecting the drive.

---

### Post by livin4th on 2012-03-08
oh good to know that... its an internal disk by the way..

---

### Post by jerome1232 on 2012-03-08
[COLOR="Red"][/COLOR]In that case it would be a good idea to add an fstab entry to make the mount permanent (ie, get's mounted during boot time)

You would open the fstab file with geidt,
```
gksu gedit /etc/fstab
```
then add a line like this at the bottom, change the part in red to be where ever you want it
```
/dev/sda6 [COLOR="Red"]/mydrive[/COLOR] ntfs defaults,umask=000 0 0
```

make sure to create the folder you want it to mount in
Once you have all that done, unmount the partition from it's current location, then run mount -a to mount it via your fstab rules to make sure your fstab is right.

```
sudo mkdir [COLOR="Red"]/mydrive[/COLOR]
sudo umount /dev/sda6
sudo mount -a
```

if mount -a returns any errors repost them here

---

