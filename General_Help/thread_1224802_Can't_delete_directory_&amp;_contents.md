---
title: "Can't delete directory &amp; contents"
date: 2009-07-27
forum: General Help
---

### Post by Alligator on 2009-07-27
I thought this would be simple.  However - rm -rf disk-1 doesn't work.
Also with sudo and various combinations with/out sudo, such as
rm -rf ./disk-1, rm -rf "disk-1", rm -rf /media/disk-1, rm -rf -- disk-1

disk-1 is the name given to a partition on a usb drive during auto mount. I've been working on a script to auto detect usb drive and write a backup file to disk-1. The script created a second disk-1, the original unmounted as expected leave the one that will not go away.

Also, can't enter the directory or move it. With the file manager, Places -> /media/disk-1 the file folders are displayed with an X in them, not allowing access.

This is a first for me.  How do I get rid of the directory tree?

Ron

---

### Post by ratcheer on 2009-07-27
I think the proper command is

```
rm -Rf TheDirname
```

Of course, you have to have the permissions on the directory and all the files in it.

Tim

---

### Post by jenkinbr on 2009-07-27
Open a terminal

```
cd /media/disk-1
sudo rm -rf ./*

```

If that does not work, perhaps there is a hardware write lock on the device?

---

### Post by Alligator on 2009-07-27
> **jenkinbr said:**
> Open a terminal

```
cd /media/disk-1
sudo rm -rf ./*

```

If that does not work, perhaps there is a hardware write lock on the device?

The cd cmd results in error - no such file or directory.  The hardware is a laptop.  What next?

---

### Post by jenkinbr on 2009-07-27
> **Alligator said:**
> The cd cmd results in error - no such file or directory.  The hardware is a laptop.  What next?
```
ls -la /media/
```

---

### Post by Alligator on 2009-07-28
> **jenkinbr said:**
> ```
ls -la /media/
```

drwxr-xr-x 47 ronh ronh 4096 2009-07-27 11:45 disk-1

---

### Post by jenkinbr on 2009-07-28
> **Alligator said:**
> drwxr-xr-x 47 ronh ronh 4096 2009-07-27 11:45 disk-1
ls -la /media/disk-1/

---

### Post by Alligator on 2009-07-28
> **jenkinbr said:**
> ls -la /media/disk-1/

ls: cannot access /media/disk-1 : No such file or directory

---

### Post by jenkinbr on 2009-07-28
This is very odd, very odd indeed....

Try

```
df -h
```

---

### Post by niteshifter on 2009-07-28
Hi,

Might be locked (by a process that hasn't completed). What does
```
fuser /media/disk-1
```
produce?

---

### Post by Alligator on 2009-07-28
> **niteshifter said:**
> Hi,

Might be locked (by a process that hasn't completed). What does
```
fuser /media/disk-1
```
produce?

Cannot stat /media/disk-1: No such file or directory

---

### Post by Alligator on 2009-07-28
> **Alligator said:**
> Cannot stat /media/disk-1: No such file or directory

df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.2G  4.9G  3.9G  56% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  304K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  168K  1.9G   1% /dev
tmpfs                 1.9G  480K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda1             281G   21G  247G   8% /home
/dev/sdc1             3.9G  4.3M  3.9G   1% /media/disk
/dev/sr1              5.6M  5.6M     0 100% /media/U3System
Note: sdc is a usb drive

---

### Post by niteshifter on 2009-07-28
Hi,

Which device has /media/disk-1?

---

### Post by jenkinbr on 2009-07-28
> **Alligator said:**
> df -h 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.2G  4.9G  3.9G  56% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  304K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  168K  1.9G   1% /dev
tmpfs                 1.9G  480K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda1             281G   21G  247G   8% /home
[COLOR="Cyan"]/dev/sdc1             3.9G  4.3M  3.9G   1% /media/disk[/COLOR]
[COLOR="Lime"]/dev/sr1              5.6M  5.6M     0 100% /media/U3System
```[/COLOR]
Note: sdc is a usb drive

You appear to not have any /media/disk-1 devices, however, you do have /media/disk (as seen in the cyan highlight above).

By combining the Cyan and the lime output, it appears you have a Sandisk Cruiser Micro (or something along those lines) that contains U3 software. Can you confirm this?

I have had problems with this software in the past.  If you have access to a machine with windows, I suggest removing the U3 software. If you need portable windows applications like those provided by U3, [http://portableapps.org](http://portableapps.org) has a large selection of such apps.

---

### Post by Alligator on 2009-07-28
> **jenkinbr said:**
> You appear to not have any /media/disk-1 devices, however, you do have /media/disk (as seen in the cyan highlight above).

By combining the Cyan and the lime output, it appears you have a Sandisk Cruiser Micro (or something along those lines) that contains U3 software. Can you confirm this?

I have had problems with this software in the past.  If you have access to a machine with windows, I suggest removing the U3 software. If you need portable windows applications like those provided by U3, [http://portableapps.org](http://portableapps.org) has a large selection of such apps.

It turns out that my script was putting a space at the end of disk-1. The directory disk-1 is now removed and the cyan and lime lines are also removed from df -h  

Thanks for the assistance
Ron

---

