---
title: "rsync -x option?"
date: 2011-01-26
forum: General Help
---

### Post by garyed on 2011-01-26
I've read the man pages & searched online to figure out what the -x option does in the rsync command but I still don't get it.
Can someone explain in simple terms what this means: 
>  -x, --one-file-system
 This tells rsync to avoid crossing a filesystem boundary when recursing.  This does not limit the user’s ability to specify items to copy from multiple filesystems, just  rsync’s  recursion  through  the hierarchy of each directory that the user specified, and also the analogous recursion on the receiving side during deletion.  Also keep in mind that rsync treats a "bind" mount to the same device as being on the same filesystem.....


---

### Post by amra.sonntag on 2011-01-26
If i get it right - it behaves like this.

Say you got a disk mounted somewhere in /home - like /home/user/*/*/disk. And now you use rsync with -x on /home (with the option to go recursive through it), it will stop at disk and not enter it - since it is another filesystem.

---

### Post by cipherboy_loc on 2011-01-26
Also, if you have the following mounting format:

/  - /dev/sda1
/home - /dev/sda2
/home/ubuntu - /dev/sdb1
/boot - /dev/sda3

and you run:

```

rsync -x --recursive /  /home    /mnt/backups

```

it would copy the contents of / and /home, but not /boot nor /home/ubuntu, to /mnt/backups. Spaces added for emphasis.



Cipherboy

---

### Post by garyed on 2011-01-27
So lets see if I've got it.
Any partition that is mounted is considered a file system boundary & will not be copied if -x is used unless it is in the rsync command line.
Now I have mounted:
 sda6 /
 sda7 /home
 sda1 /media/gusty
 sdb1  /media/windows
 sdc1 /media/hitachi
I want to copy sda6  to sdc1 so i use:
> rsync -ax / /media/hitachi
Everything under / will be copied except for sda1,sda7,& sdb1 .
Is that right?

---

### Post by amra.sonntag on 2011-01-27
I believe it would do just that. But you can allways use -n to make a dryrun - just to find out if it does what you want it to do.

---

### Post by garyed on 2011-01-27
> **garyed said:**
> So lets see if I've got it.
Any partition that is mounted is considered a file system boundary & will not be copied if -x is used unless it is in the rsync command line.
Now I have mounted:
 sda6 /
 sda7 /home
 sda1 /media/gusty
 sdb1  /media/windows
 sdc1 /media/hitachi
I want to copy sda6  to sdc1 so i use:

Everything under / will be copied except for sda1,sda7,& sdb1 .
Is that right?

Well I did it & it copied everything exactly as I understood it.
Thanks to all for the help.

---

