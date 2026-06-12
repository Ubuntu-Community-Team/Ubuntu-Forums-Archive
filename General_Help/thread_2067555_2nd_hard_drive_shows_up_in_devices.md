---
title: "2nd hard drive shows up in devices?"
date: 2012-10-07
forum: General Help
---

### Post by qwertyjjj on 2012-10-07
I added a 2nd 2TB hard drive and mounted it to /media/mynewharddrive
However, it shows up in devices on nautilus.
Also, it seems to be owned by root, so do I change the mount permissions or something else? I cannot create files on the drive at the moment.

```

$ df
Filesystem                     1K-blocks      Used  Available Use% Mounted on
/dev/sda1                      957563524 812553656   96368384  90% /
udev                             1922440         4    1922436   1% /dev
tmpfs                             773052      1188     771864   1% /run
none                                5120         0       5120   0% /run/lock
none                             1932624       376    1932248   1% /run/shm
/dev/sdb1                     1922859824    200160 1824983992   1% /media/mynewdrive
/home/j-media-centre/.Private  957563524 812553656   96368384  90% /home/j-media-centre

```

```

$ ls -l /media/
total 8
drwxr-xr-x 2 root root 4096 Jun 13 19:47 iomega
drwxr-xr-x 3 root root 4096 Oct  5 16:57 mynewdrive
j-media-centre@jmediacentre-A880G:~$ ls -l /media/mynewdrive
total 16
drwx------ 2 root root 16384 Oct  5 16:57 lost+found
j-media-centre@jmediacentre-A880G:~$ 

```

ALso, why does it show up as a new device? The 1st hard drive doesn#t appear anywhere and is mounted to /
How can I have this hard drive appear seamless within the system without it showing up as a device? Can#t I mount it to / as well or have a symlink from / to /media/mynewdrive?

---

### Post by surfer on 2012-10-07
does this help?
[LIST]
[*][http://askubuntu.com/questions/62011/how-do-i-remove-mounted-drives-from-the-unity-launcher](http://askubuntu.com/questions/62011/how-do-i-remove-mounted-drives-from-the-unity-launcher)

[*][http://www.webupd8.org/2011/04/how-to-remove-mounted-drives-from.html](http://www.webupd8.org/2011/04/how-to-remove-mounted-drives-from.html)
[/LIST]

---

### Post by powerpleb on 2012-10-07
Devices mounted in /media will always show up in file managers, it is what /media is for.

If you want to mount a device somewhere that won't show up, mount in in the /mnt directory.

As for permissions, you can set them when you mount the drive. How are you doing this? From the command line or are you using fstab?

For example, to mount it with read/write privileges for users from the command line (this should be default anyway):```
sudo mount /dev/sdx1 /mnt/drivename -rw
```

Similarly in fstab, add "rw" to the list of options:
```
/dev/sdx1 /mnt/drivename ext4 defaults,**rw **1 1
```

If it still doesn't work. It's probably that the permissions for that file or directory aren't set right. In that case you need to change them like so.
```
sudo chmod -R 775 /mnt/drivename
```

Hope that helps.

---

