---
title: "How to mount a separate partition automatically at start-up?"
date: 2009-11-06
forum: General Help
---

### Post by Pipps on 2009-11-06
My Ubuntu is installed at sda3. Windose installed at sda1.

When in Ubuntu, I would like to have automatic access the XP *My Documents* folder, without having to ask Ubuntu to mount or auto-mount sda1 when I first try to access it.

Is there a way to set Ubuntu to auto-mount a separate partition at startup?

---

### Post by t.rei on 2009-11-06
If your windows is on an ntfs partition:
sudo apt-get install ntfs-config
sudo ntfs-config

thats probably the easiest way to get your partitions entered into the /etc/fstab

---

### Post by HiImTye on 2009-11-06
you can manually add it to your fstab file by doing the following:
```
gksu gedit /etc/fstab
```
or you can use a graphical tool by doing the following:

[LIST=1]
[*]```
sudo apt-get install pysdm
```
[*]system>administration>storage device manager
[/LIST]
this will give you a pretty easy to use tool

---

### Post by amauk on 2009-11-06
decide where you want to mount the windows partition
say, /media/windows
then create a directory for it
```
sudo mkdir /media/windows
```

open up the file system table as root
```
sudo gedit /etc/fstab
```

add an entry for your windows partition
```
/dev/sda1  /media/windows  ntfs  defaults,user  0  0
```

---

### Post by HiImTye on 2009-11-06
> **amauk said:**
> decide where you want to mount the windows partition
say, /media/windows
then create a directory for it
```
sudo mkdir /media/windows
```open up the file system table as root
```
sudo gedit /etc/fstab
```add an entry for your windows partition
```
/dev/sda1  /media/windows  ntfs  defaults,user  0  0
```

use this method, however, find out the device location using partition editor/gparted (system>administration>) it will be in the top right as a pull down menu. use this path (for instance /dev/sdb1) at the beginning of your fstab entry

---

### Post by Pipps on 2010-01-07
Allow me to confirm that I have understand your excellent advice correctly:

So if I wanted to mount '/media/HD2_Media' which is otherwise known as '/dev/sdb1', then I would add the following to fstab:

> /dev/sdb1  /media/HD2_Media  ntfs  defaults,user  0  0

Would this be correct?

---

### Post by amauk on 2010-01-07
> **Pipps said:**
> Would this be correct?yes

---

### Post by Pipps on 2010-01-07
Thank you! :)

---

### Post by Pipps on 2010-01-07
A problem seems to have arisen.

Immediately following reboot, sdb1 does not mount at all, and when I try to mount it manually in nautilus, I receive the following error message;

> **Unable to mount HD2_Media:**
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

What could I have done wrong? :confused:

---

### Post by michy99 on 2010-01-07
Post the output from these commands.```
cat /etc/fstab
sudo fdisk -l
mount
ls -l /media
```

---

### Post by Pipps on 2010-01-07
Please find below the output to the four commands as instructed:

**cat /etc/fstab**
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=87732a5b-38cb-4548-b619-9a1dbed5827d /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda4 during installation
UUID=de80de10-1886-41d0-97c3-2805b72cfe06 /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=72e20516-e44c-4c01-9afb-deff5ac0e129 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/HD2_Media ntfs defaults,user 0 0 


**sudo fdisk -l**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedf4edf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3608    28981228+   7  HPFS/NTFS
/dev/sda2           57985       60789    22531162+  83  Linux
/dev/sda3            3609       57984   436775220    5  Extended
/dev/sda4           60790       60801       96390   83  Linux
/dev/sda5            3609       57856   435747028+  83  Linux
/dev/sda6           57857       57984     1028128+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cd17c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table


**mount**
> /dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda4 on /boot type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pipps/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pipps)
/dev/sda5 on /media/359291d9-e9bc-4ed7-987a-30299b5629bb type ext3 (rw,nosuid,nodev,uhelper=devkit)


**ls -l /media**
> total 8
drwxr-xr-x 3 root root 4096 2010-01-07 22:20 359291d9-e9bc-4ed7-987a-30299b5629bb
lrwxrwxrwx 1 root root    6 2010-01-02 00:12 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-01-02 00:12 cdrom0


I hope you wouldn't mind interpreting all this for me! :)

---

### Post by oldfred on 2010-01-07
The link you provided had this comment:
[B][B]Why don&#8217;t the &#8216;user&#8217; and &#8216;users&#8217; options work in /etc/fstab?

[/B][FONT=Georgia]and my entry has no user

# Entry for /dev/sda2 :
UUID=2A87EC53669130A9                      /home/fred/shared  ntfs-3g      defaults                             0  0  

Also after you change fstab do this as you do not have to reboot and it will tell you if you have any errors:

sudo mount -a
[/FONT] [/B]

---

### Post by michy99 on 2010-01-07
I see several things here. First, fdisk shows sdb1 as being a Linux partition, but you are trying to mount it as ntfs. Second, you are trying to mount to a mountpoint that doesn't exist. So the first question is, what is the filesystem of sdb1? is it ext3 or ext4?

---

### Post by Pipps on 2010-01-07
The filesystem of sdb1 is ext3.

Ah. I see the problem now.

Should I change the 'ntfs' to 'ext3' in the command in post 6 above?

---

### Post by Pipps on 2010-01-07
I have changed the 'ntfs' to 'ext3' in the fstab entry, and I now receive the following error message:

> **Unable to mount HD2_Media**
Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/HD2_Media does not exist

As you point out, Michy99, a mount-point which does not exist!

Edit: Would it be possible to mount HD2_Media at its very top point?

---

### Post by amauk on 2010-01-07
(deleted)

---

### Post by michy99 on 2010-01-07
Ok, the line in your /etc/fstab is wrong. It should be```
/dev/sdb1 /media/HD2_Media  ext3    defaults        0       2
```Also, you need to make the mount point.```
sudo mkdir /media/HD2_Media
sudo chown PUT_YOUR_USERNAME_HERE:users /media/HD2_Media
```Reboot and see if it works. I have to eat dinner so I will check back later.

---

### Post by Pipps on 2010-01-07
It works perfectly now! :D

Thank you Michy!!! :D

---

### Post by HiImTye on 2010-01-07
> **michy99 said:**
> Ok, the line in your /etc/fstab is wrong. It should be```
/dev/sdb1 /media/HD2_Media  ext3    defaults        0       2
```Also, you need to make the mount point.```
sudo mkdir /media/HD2_Media
sudo chown PUT_YOUR_USERNAME_HERE:users /media/HD2_Media
```Reboot and see if it works. I have to eat dinner so I will check back later.
thank you for adding the '2' - I was going to comment about it but alas, I just got home since sunday :D

---

### Post by Treepwood on 2010-01-08
Is there a way to do this, without automatically having an icon placed on the desktop, with the mounted device?

---

### Post by Pipps on 2010-01-08
> **Treepwood said:**
> Is there a way to do this, without automatically having an icon placed on the desktop, with the mounted device?

Yes, I would like to know this too!

I would prefer the auto-mounting to be made available at each boot, without a picture of the drive being placed on the desktop.

Would this be more of a desktop presentation issue, in gconf-editor?

---

### Post by Pipps on 2010-01-08
> **HiImTye said:**
> 
thank you for adding the '2' - I was going to comment about it but alas, I just got home since sunday :D

Incidentally, for the purposes of future reference, what is the difference between the '0' and the '2' in this context?

Either:

> /dev/sdb1 /media/HD2_Media  ext3    defaults        0       0

or 

> /dev/sdb1 /media/HD2_Media  ext3    defaults        0       2

What is the difference?

---

### Post by Maheriano on 2010-01-08
marked to do on my machine as well.

---

### Post by Morbius1 on 2010-01-08
> Incidentally, for the purposes of future reference, what is the difference between the '0' and the '2' in this context?The last digit determines whether or not linux does a filesystem check at boot. "0" means no, a "1", or "2" means yes.

> I would prefer the auto-mounting to be made available at each boot, without a picture of the drive being placed on the desktop.Any mount pioint in /home or /media produces an icon. Any mount point in /mnt or / does not.

---

### Post by Pipps on 2010-01-08
So if I just created a directory called /mnt/HD2_Media, and then referenced the relevant fstab entry to this, then I would still be automatically mounted at system startup, but would not see an unnecessary icon appearing on the desktop?

---

### Post by Morbius1 on 2010-01-08
It should. Just remember to redo the steps michy99 told you about concerning chown on the new /mnt/HD2_Media directory.

When your done creating the new mount point and making the modification in fstab to reflect the new mount point, try this to save yourself a reboot:

Open **Terminal**
Type **sudo umount /media/HD2_Media**
Type **sudo mount -a**

---

### Post by Pipps on 2010-01-08
Thanks for reminding me! Phew!

And thank you for the great tip! :D

---

