---
title: "Move /home to larger hard drive"
date: 2011-06-19
forum: General Help
---

### Post by bschuteker on 2011-06-19
I'm sure that this is posted somewhere but I have not been able to find the right search terms. I have a Dell Vostro 1700 which has 2 physical hard drives. I installed Natty to the 1st drive and during the install I used the entire 2nd drive as /home. I would like to upgrade the 2nd drive to a larger faster drive. I have the new drive in a USB enclosure so that I can access both drives. I'm pretty sure I need to boot from the CD to do this. Then  I need to copy all files unmount the small drive then shut down, install the larger drive and have the system recognize it as /home. I am just starting to creep out of N00B stage and don't want to screw this up. If someone could please point me to the correct link or give me step by step instructions I would be most appreciative.

Thanks,

Bill

---

### Post by bschuteker on 2011-06-21
Anyone???

---

### Post by doas777 on 2011-06-21
you already have the gist of it, the only think missing is reconfiguring your fstab. 

here is some good info on fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

1) format your new drive with ext4 or whatever FS you choose.

2) boot off a live cd, mount your current home, and your new one, and copy the data from old to new. 

3) shutdown, and install your new drive, removing the old one. keep it arround in a safe place for a little while just in case. 

4) boot to live CD again, and mount your root partition.

5) open for editing your /etc/fstab with your text editor of choice.

6) find the line that mounts your home. here is an excerpt of mine with teh home line highlighted:
```

Lucid:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c36420d9-2fc0-4012-bfeb-4fe23d78b430 /               ext4    errors=remount-ro,acl 0       1
# /home was on /dev/sdb1 during installation
**UUID=e5d4440a-dd76-4b44-91f9-f7d888b221dc /home           ext4    defaults,acl        0       2**
# swap was on /dev/sda5 during installation
UUID=677c12dd-caea-49c5-857e-5663c152250a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

7) in a seperate terminal run 
```
ls -l /dev/disk/by-uuid

```
and find the UUID of your new volume.

8) in your fstab, replace the UUID for your home line to the new one. if your filesystem type is differant, change that parameter too.

9) save fstab, shutdown , remove teh live CD and boot off your installed os. now, it should be using your new home. 

10) if you see permissions errors regarding your home, try running these commands, to reset teh default owner and permissions for your home:
```
sudo chown -R <username>:<username> /home/<username>

sudo chmod -R 640 /home/<username>
```

and that shoudl do you.

---

