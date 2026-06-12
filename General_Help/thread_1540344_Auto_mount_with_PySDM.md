---
title: "Auto mount with PySDM"
date: 2010-07-27
forum: General Help
---

### Post by gavdari on 2010-07-27
I wanted to auto mount one of my drives at the startup so I installed PySDM. After that every time I login to Ubuntu every single drive is mounted with a new name, for example one of my drives was located at /media/Local Disk and now it's /media/sda6, so every link to that drive including my audio library is gone. I unchecked the 'auto-mount at startup' option in PySDM and it didn't solve anything, I even uninstall PySDM and it everything is mounted as soon as Ubuntu starts up. The funny thing is there is a 10GB recovery drive on my hard disk that was never visible in Ubuntu and I was happy with that, but now it is mounted on startup too, with the name of sda1. What should I do?

---

### Post by gavdari on 2010-07-27
I did some digging around and found out that my fstab file is messed up so bad. now I have to login as root to be able to mount a drive. here's fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda7 during installation
UUID=37a593aa-f7f4-49a6-90f6-3926bea80590  /                 ext4  errors=remount-ro    0  1  
# swap was on /dev/sda8 during installation
UUID=810a447c-938a-4486-a8fe-0781b07c3fa5  none              swap  sw                   0  0  
/dev/sda1                                  /media/Recovery   ntfs  defaults             0  0  
/dev/sda5                                  /media/Windows    ntfs  defaults             0  0  
/dev/sda6                                  /media/Local Disk  ntfs  nls=iso8859-1,ro,umask=000         0  0  
/dev/sda6                                  /media/Local Disk  ntfs  nls=iso8859-1,ro,umask=000         0  0  
/dev/sda6                                  /media/LocalDisk  ntfs  defaults             0  0  
```
What should I do to make it right?

---

### Post by sisco311 on 2010-07-27
So, you want to mount sda5 (the Windows partition) and sda6 (Local Disk), right?

Do you want to mount them read only or with write permissions?

---

### Post by gavdari on 2010-07-27
I could mount them without any problem with write permission. but now first of all they all get mounted when Ubuntu startsup, the address is changed from /media/Local Disk to /media/sda6 and it gives me this when I try to mount it:
```
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda6 on /media/Local_Disk
```

---

### Post by sisco311 on 2010-07-27
Back up fstab:
```
sudo cp /etc/fstab{,-backup}
```

Find out the UUID of the partitions:
```
sudo blkid -o list -c /dev/null /dev/sda{5,6}
```

Open fstab for editing:
```
gksu gedit /etc/fstab
```

Delete the last 5 lines and append the file with:
```

UUID=**<copy the UUID of sda5 here>**    /media/Windows    ntfs    defaults,gid=plugdev,dmask=002,fmask=113    0    0

UUID=**<copy the UUID of sda6 here>**    /media/Local**\040**Disk    ntfs    defaults,gid=plugdev,dmask=002,fmask=113    0    0

```
NOTE: instead of the space in the mount point, in fstab you have to put **\040**.


unmount the partitions:
```
sudo umount /dev/sda{1,5,6}
```

make sure that the mount poins exist:
```
sudo mkdir -p /media/Windows
sudo mkdir -p /media/Local\ Disk
```

mount the partitions listed in fstab:
```
sudo mount -a
```

---

### Post by gavdari on 2010-07-27
I did everything. Still, I need root permission to mount/unmount sda5 and sda6. here's the error when I try to unmount Windows without root permission:
Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=36CC3005CC2FBE4D from /media/Windows

edit: I guess it's because at startup they're mounted as root, so only root can unmount them. but what should I do if I don't want them to mount at startup?

---

### Post by gavdari on 2010-07-27
besides, nothing happens when I connect my external hard drive.

edit: restarting solved this

---

### Post by mc4man on 2010-07-27
Why don't you just put your fstab back to the way it originally was before all of this

To open a partition, auto mounted or not, you still need to click on an icon.

Is there really much difference between clicking on an icon on the desktop vs. one in the 'places' menu? (that can also be user mounted and unmounted?

If so, and unsure at all how to edit back to orig. or comment out the new lines in your fstab, then post your current one and someone will advise - (you don't want to go from bad to worse

---

### Post by gavdari on 2010-07-27
you're right. there is actually no difference. but I'm trying to learn and hard disk management was one of the trickiest parts of linux for me until now. I'm learning!

p.s. I was stupid enough to forget backing up fstab before playing with it.

---

### Post by mc4man on 2010-07-27
> I'm learning!
+1 on that - one of the best ways to learn is when things don't go well and finding a way to make it  right.

---

### Post by Sim-I-Am :} on 2011-11-18
> **sisco311 said:**
> Back up fstab:
```
sudo cp /etc/fstab{,-backup}
```

Find out the UUID of the partitions:
```
sudo blkid -o list -c /dev/null /dev/sda{5,6}
```

Open fstab for editing:
```
gksu gedit /etc/fstab
```

Delete the last 5 lines and append the file with:
```

UUID=**<copy the UUID of sda5 here>**    /media/Windows    ntfs    defaults,gid=plugdev,dmask=002,fmask=113    0    0

UUID=**<copy the UUID of sda6 here>**    /media/Local**\040**Disk    ntfs    defaults,gid=plugdev,dmask=002,fmask=113    0    0

```
NOTE: instead of the space in the mount point, in fstab you have to put **\040**.


unmount the partitions:
```
sudo umount /dev/sda{1,5,6}
```

make sure that the mount poins exist:
```
sudo mkdir -p /media/Windows
sudo mkdir -p /media/Local\ Disk
```

mount the partitions listed in fstab:
```
sudo mount -a
```

I know this is old,  but I just wanted to let you know how much I appreciate this advice....worked perfectly for me!

I've always heard from people around the web things like "for those of us who aren't comfortable editing fstab ourselves, there's always pysdm or ntfs-config"(which have recently stopped working for me)....Thus, I always assumed fstab was some impossibly complex configuration file that only devs could understand. But it actually does make sense, and if you think through it a bit, it actually is rather easy to configure.

So thanks for the advice, and for helping me break out of my bubble! :D

---

