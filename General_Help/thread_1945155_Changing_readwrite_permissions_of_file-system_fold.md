---
title: "Changing read/write permissions of file-system folder?"
date: 2012-03-22
forum: General Help
---

### Post by pdr2esmolbra on 2012-03-22
Hello there, 

This is my first post, I hope this question is not too obvious :)

I have Ubuntu 10.10 Maverick Meerkat running on a double particion with Windows XP on a Hp Pavillon dv6120ca laptop.

I have most of my files on my 'E:' windows partition sitting on a folder '/dos/*' in Ubuntu. Somehow I can't seem to edit any of the files in this '/dos/' folder. 

I have tried commands like 

pedrito@pedros-HPdv6120:/$ chmod 777 /dos/
chmod: changing permissions of `/dos/': Read-only file system

The ls -l of the / folder gives

drwxrwx---  34 root plugdev 32768 1969-12-31 19:00 dos

I have googled around and apparently I need change the way the '/dos/' or the 'E:' particion is mounted on startup. But where and how to do that, I don't know?? 

Thanks a lot for your help everyone!

---

### Post by cortman on 2012-03-22
Normally Windows partitions seem to mount as /media/UUID. Did you edit fstab at all to make it mount as /dos?
I have a partition on my computer for data storage that I mount as /data, and I had to set it so in fstab. You can also set it to mount read-only or defaults in fstab as well.

---

### Post by pdr2esmolbra on 2012-03-25
> **cortman said:**
> Normally Windows partitions seem to mount as /media/UUID. Did you edit fstab at all to make it mount as /dos?

Thanks a lot for that pointer!
I went to edit the fstab, and after many attempts and reboots managed to change the permissions.

I found a GUI  that can make the process a bit clearer = PySDM. It  illuminated the fact that ```
sudo mount -a
``` might not work on particions actively used by the OS.

Thanks!

---

### Post by cortman on 2012-03-26
I don't think it's available in the Ubuntu repositories but you may be able to get it elsewhere- Disk Manager. Little GUI tool for editing fstab- works wonderfully with my Crunchbang installation, and a good bit safer than manually tweaking fstab (if you don't know what you're doing, like me. :))

---

### Post by pdr2esmolbra on 2012-03-31
Hello there again...

Actually, the problem was not solved at all!

I can change permissions and remount the particion, but it works only in the terminal. I promise this is the strangest thing that has ever happened to me!  I can create test documents and folders right when I remount my drive in the terminal, but the second I open a folder and try the same it blocks everything returning the disk to 'read-only' mode? Going back to terminal (even in SUDO!!) blocks every write action! Any idea why this happens!?

Here's my fstab line on the problematic disk:

#Entry for /dev/sda4 :
UUID=E51F-9C31   /dos   vfat     uid=1000,umask=000,gid=100,users,rw  0  0  

Here's the result of fdisk -l

/dev/sda4   9292       14594    42584064    b  W95 FAT32


Apparently 0x0b FAT is ancient but would that help?? Not sure I want to try changing that in case it screws up windows and data stored...

Mount command returns:

/dev/sda1 on /XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
pedrito@pedros-HPdv6120:~$ mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pedrito/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pedrito)
/dev/sda1 on /XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /dos type vfat (rw,noexec,nosuid,nodev,uid=1000,umask=000,gid=100,utf8)

There are some errors above but don't seem related to "/dos"=:twisted:

I am going insane! 
I am just about to reformat this particion to NTFS!

Please HELP! 

Thanks!

---

