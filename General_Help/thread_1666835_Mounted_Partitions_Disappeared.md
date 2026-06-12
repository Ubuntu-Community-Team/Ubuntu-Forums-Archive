---
title: "Mounted Partitions Disappeared"
date: 2011-01-14
forum: General Help
---

### Post by kamillas on 2011-01-14
My Laptop has Ubuntu 9.04 and I am using it for the past one year. I have four partitions. Gparted Screen Shot attached. 

/dev/sda5 was mounted as "Laptop 2"
/dev/sda6 was mounted as "Laptop 3"

But from today morning I was not able to access any of the files from my hard disk. When I press the "Computer" Menu Item from the "Places" menu I could access all the files on my hard disk. It shows an error message attached with this thread. The system boots perfectly and work perfectly. "Laptop 2" and "Laptop 3" disappeared.

I searched the net and found ways to mount the Partitions with these following commands.

sudo nano /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=5bde3d93-93f6-4852-8fc4-f8f6780ffc52 /               ext4    relatime,erro$
# swap was on /dev/sda3 during installation
UUID=1990616c-2cc4-4fc6-9ab6-e247be064c8f none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0




#I added the following three lines to the file.



/dev/sda1       /media/Laptop_1 ext4 defaults 0 0
/dev/sda5       /media/Laptop_2 ext4 defaults 0 0
/dev/sda6       /media/Laptop_3 ext4 defaults 0 0



Then I used

sudo mount -a


to mount the partitions and it worked. An I was able to see and open the partition from the "Places" menu a.

I still get the same error message when I press "Computer" on the "Places" menu. I am not able to Mount the partitions with the names "Laptop 2" and "Laptop 3" as it was earlier.

I tried changing those three lines as follows and none worked.

/dev/sda1       /media/"Laptop 1" ext4 defaults 0 0
/dev/sda5       /media/"Laptop 2" ext4 defaults 0 0
/dev/sda6       /media/"Laptop 3" ext4 defaults 0 0

and this

/dev/sda1       /media/Laptop\ 1 ext4 defaults 0 0
/dev/sda5       /media/Laptop\ 2 ext4 defaults 0 0
/dev/sda6       /media/Laptop\ 3 ext4 defaults 0 0

and this

/dev/sda1       "/media/Laptop 1" ext4 defaults 0 0
/dev/sda5       "/media/Laptop 2" ext4 defaults 0 0
/dev/sda6       "/media/Laptop 3" ext4 defaults 0 0

I get the following error when i run "sudo mount -a"

[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad

Is there any way I could use "Laptop 2" and "Laptop 3" as my mount points as it was earlier.

---

### Post by TeoBigusGeekus on 2011-01-14
See if any of the solutions proposed [here]("http://ubuntuforums.org/showthread.php?t=801597&page=8") are good for you.

---

### Post by TeoBigusGeekus on 2011-01-14
See if any of the solutions proposed [here]("http://ubuntuforums.org/showthread.php?t=801597&page=8") are good for you.

---

### Post by tredegar on 2011-01-14
> I get the following error when i run "sudo mount -a"

[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 17 in /etc/fstab is bad


So your **/etc/fstab** is "bad".

If you posted it, we could take a look at it, and perhaps tell you how to fix it.

Please also tell us the output of ```
ls -l /media
```

---

### Post by tredegar on 2011-01-14
Warning: OFF-TOPIC, so deel free to scroll on down...

EDIT:
Another **** double post.

Firefox replied:
> Proxy Error

The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request POST /newreply.php.

Reason: Error reading from remote server

[COLOR="Red"]Apache/2.2.8 (Ubuntu)[/COLOR] Server at ubuntuforums.org Port 80 
So I did "Back" and then "Submit Reply"

This forum is BROKEN.
But then, it's running ubuntu, so what _should_ I expect?

---

### Post by kamillas on 2011-01-14
> **tredegar said:**
> So your **/etc/fstab** is "bad".

If you posted it, we could take a look at it, and perhaps tell you how to fix it.

Please also tell us the output of ```
ls -l /media
```
total 48
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 3
lrwxrwxrwx 1 root root    6 2010-06-18 00:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 cdrom0
lrwxrwxrwx 1 root root    7 2010-06-18 00:02 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 floppy0
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 1
drwxr-xr-x 2 root root 4096 2011-01-14 16:20 Laptop_1
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 3
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_3
drwx------ 2 root root 4096 2010-08-08 16:44 WD SmartWare

---

### Post by kamillas on 2011-01-14
> **tredegar said:**
> So your **/etc/fstab** is "bad".

If you posted it, we could take a look at it, and perhaps tell you how to fix it.

Please also tell us the output of ```
ls -l /media
```
total 48
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 3
lrwxrwxrwx 1 root root    6 2010-06-18 00:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 cdrom0
lrwxrwxrwx 1 root root    7 2010-06-18 00:02 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 floppy0
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 1
drwxr-xr-x 2 root root 4096 2011-01-14 16:20 Laptop_1
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 3
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_3
drwx------ 2 root root 4096 2010-08-08 16:44 WD SmartWare

---

### Post by kamillas on 2011-01-14
> **tredegar said:**
> So your **/etc/fstab** is "bad".

If you posted it, we could take a look at it, and perhaps tell you how to fix it.

Please also tell us the output of ```
ls -l /media
```
total 48
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 3
lrwxrwxrwx 1 root root    6 2010-06-18 00:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 cdrom0
lrwxrwxrwx 1 root root    7 2010-06-18 00:02 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 floppy0
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 1
drwxr-xr-x 2 root root 4096 2011-01-14 16:20 Laptop_1
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 3
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_3
drwx------ 2 root root 4096 2010-08-08 16:44 WD SmartWare

---

### Post by kamillas on 2011-01-14
> **tredegar said:**
> So your **/etc/fstab** is "bad".

If you posted it, we could take a look at it, and perhaps tell you how to fix it.

Please also tell us the output of ```
ls -l /media
```
total 48
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 3
lrwxrwxrwx 1 root root    6 2010-06-18 00:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 cdrom0
lrwxrwxrwx 1 root root    7 2010-06-18 00:02 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 floppy0
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 1
drwxr-xr-x 2 root root 4096 2011-01-14 16:20 Laptop_1
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 3
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_3
drwx------ 2 root root 4096 2010-08-08 16:44 WD SmartWare

---

### Post by kamillas on 2011-01-14
> **tredegar said:**
> So your **/etc/fstab** is "bad".

If you posted it, we could take a look at it, and perhaps tell you how to fix it.

Please also tell us the output of ```
ls -l /media
```
total 48
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 3
lrwxrwxrwx 1 root root    6 2010-06-18 00:02 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 cdrom0
lrwxrwxrwx 1 root root    7 2010-06-18 00:02 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-06-18 00:02 floppy0
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 1
drwxr-xr-x 2 root root 4096 2011-01-14 16:20 Laptop_1
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 2
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_2
drwxr-xr-x 2 root root 4096 2011-01-14 16:33 Laptop 3
drwxr-xr-x 2 root root 4096 2011-01-14 16:00 Laptop_3
drwx------ 2 root root 4096 2010-08-08 16:44 WD SmartWare

---

