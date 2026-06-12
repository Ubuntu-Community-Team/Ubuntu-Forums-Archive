---
title: "Windows NTFS partition(HDD) marked as read-only"
date: 2009-09-01
forum: General Help
---

### Post by glubbdrubb on 2009-09-01
For a long time I had no problems after installing Karmic.

I think I may have made a change to the /etc/fstab file, but I don't know what I did wrong.

I have tried to rectify this problem as root by right-clicking the the files in the partion and modifying the permissions but it does not work.


Here is the out-put for my fstab file:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                         0  0  
# / was on /dev/sda1 during installation
UUID=2653bea7-bfc4-4ed7-80fd-5f1003216b9b  /              ext3         relatime,errors=remount-ro       0  1  
# swap was on /dev/sda5 during installation
UUID=5616b4de-a32f-46c9-8b25-32254b8217d8  none           swap         sw                               0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8            0  0  
none                                       /proc/bus/usb  usbfs        devgid=124,devmode=664           0  0  
/dev/sda3                                  /media/sda3    ext3         errors=remount-ro,user           0  0  
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,ro,umask=000,user  0  0  
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

```

That  last line is a modification I have made so the usb works in virtual box.

I have two internal HDD's. The NTFS partion is obviously Windows.
Then I partitionedthe other HDD into two halves.

What must I do so I can write to the windows HDD?

---

### Post by thinkdez on 2009-09-01
Its been a while since I played with ntfs but it seems you are not using the ntfs-3g driver to mount the ntfs partition.

Make sure the the driver is installed: ```
sudo dpkg -l|grep ntfs-3g
```
This should produce the following
```
~$ sudo dpkg -l|grep ntfs-3g
rc  libntfs-3g12                              1:1.913-2ubuntu1                     ntfs-3g filesystem in userspace (FUSE) libra
rc  libntfs-3g23                              1:1.2216-1ubuntu2                    ntfs-3g filesystem in userspace (FUSE) libra
rc  libntfs-3g28                              1:1.2506-1ubuntu2                    ntfs-3g filesystem in userspace (FUSE) libra
ii  libntfs-3g49                              1:2009.2.1-0ubuntu2                  ntfs-3g filesystem in userspace (FUSE) libra
[COLOR="Red"]ii  ntfs-3g                                   1:2009.2.1-0ubuntu2                  read-write NTFS driver for FUSE[/COLOR]

```

If you do not see ntfs-3g installed then run ```
sudo apt-get update
``` followed by ```
sudo apt-get install ntfs-3g
```

This installs the driver for ntfs-3g

Once this is done you can mount the ntfs partition.

Try ```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```

Your drive should now be mounted read/write, however if you reboot the system will not mount the disk. 

Backup and edit your fstab file
```
sudo cp /etc/fstab /etc/fstab.bak
sudo vi /etc/fstab

```

```
Change the following line:
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,ro,umask=000,user  0  0  

To read:
/dev/sdb1                                  /media/sdb1    ntfs-3g         nls=iso8859-1,ro,umask=000,user  0  0  
```

That's it. Reboot to check the drive should mount automatically on boot. 

Hope that helps

---

### Post by drs305 on 2009-09-01
> **glubbdrubb said:**
> For a long time I had no problems after installing Karmic.

I think I may have made a change to the /etc/fstab file, but I don't know what I did wrong.

```


/dev/sdb1 /media/sdb1  ntfs  nls=iso8859-1,[COLOR="DarkRed"]**ro**[/COLOR],umask=000,user  0  0  
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

```

That  last line is a modification I have made so the usb works in virtual box.

I have two internal HDD's. The NTFS partion is obviously Windows.
Then I partitionedthe other HDD into two halves.

What must I do so I can write to the windows HDD?

If this is the ntfs drive you are referring to, you have it mounted "ro" - read only.
Remove the "ro". You can also add "uid=1000" to make yourself the owner at mounting. You can check to make sure you are user 1000 with the "id" command.
> 
/dev/sdb1                                  /media/sdb1    ntfs         nls=iso8859-1,[COLOR="DarkRed"]**uid=1000**[/COLOR],umask=000,user  0  0  
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0

Note: The reason you weren't able to modify the permissions is that they are set at the time of mounting for non-linux file systems. Commands to change the permissions after mounting will not work.

"ntfs" and "ntfs-3g" are interchangable in jaunty's fstab.

---

### Post by glubbdrubb on 2009-09-01
Thanks drs305, it worked.

This is what keeps me at ubuntu, no matter how much I mess up my system, there is always someone around to help me fix it.

And the more this happens, the more I learn, and the more I learn, the more I can help others.

---

