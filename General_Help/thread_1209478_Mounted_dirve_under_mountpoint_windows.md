---
title: "Mounted dirve under mountpoint /windows"
date: 2009-07-10
forum: General Help
---

### Post by shutdown on 2009-07-10
Hey ,
I just installed a copy of jaunty . I had this 50 GB drive which I formatted in FAT32 , so it could be used by both windows and ubuntu , but during installation I mounted it under the mount point /windows , now it shows up in the Filesystem as a folder called "Windows" but not on the desktop as a drive like it used to . I dont have windows on my computer right now ( might install it later ) , so I dont know if Windows can see it , but I would really like it back the way it used to be . 

Can someone help ? 

thanks , 
Jit

---

### Post by drs305 on 2009-07-10
Partitions mounted in /media will be visible on the Desktop. Change fstab so the mount point is /media/windows instead of /windows.

Make the mount point, then make yourself the owner (although ownership is actually established on mounting):
```

sudo mkdir /media/windows
sudo chown -R *yourusername:* /media/windows
*# to edit fstab*
sudo cp /etc/fstab /etc/fstab.bak  # Make backup of fstab
gksudo gedit /etc/fstab  # Open fstab for editing

```

Once you have made the changes:
```

sudo umount -a  # Unmount partition, disregard 'busy' messages
sudo mount -a  # Mount fstab entries. If no error messages, mounted on /media/windows.

```

---

### Post by DouglasCaixeta on 2009-07-10
I'm having a similar problem. During the installation I configure to mount my windows partition on /mnt/windows, cause I don't want to see it on Desktop.

Then I installed Windows, after Linux, and now Linux is mounting in /media/disk. How can I make it to mount on /mnt/windows again?

The strange thing is that the entry on my /etc/fstab is correct:

> # /mnt/windows was on /dev/sda3 during installation
UUID=3F97-FC5F  /mnt/windows    vfat    utf8,umask=007,gid=46 0       1

What is wrong?

---

### Post by shutdown on 2009-07-10
thanks a lot 
that solved the problem .
jit

---

### Post by drs305 on 2009-07-10
> **DouglasCaixeta said:**
> I'm having a similar problem. During the installation I configure to mount my windows partition on /mnt/windows, cause I don't want to see it on Desktop.
Then I installed Windows, after Linux, and now Linux is mounting in /media/disk. How can I make it to mount on /mnt/windows again?
The strange thing is that the entry on my /etc/fstab is correct:
What is wrong?

The windows partition should be listed in fstab. Has the UUID of the windows partition changed? You can check with this command:
```
sudo blkid | grep "ntfs"  # run as "sudo blkid" if get no results
```

You can also check to see if all your non-system fstab settings are working by doing this:
Close your applications, then:
```

sudo umount -a  
# unmounts all non-system partitions in fstab (disregard 'busy' messages.
sudo mount -a  # Mounts listings in fstab

```
If you get no error messages, everything is listed/mounted correctly.
If an fstab entry is incorrect, the error message will tell you.

---

### Post by DouglasCaixeta on 2009-07-10
Thanks, that was the problem. The UUID changed.

;)

---

