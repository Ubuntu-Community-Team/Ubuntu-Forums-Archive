---
title: "Trouble Mounting partitions--can't write to subfolders"
date: 2006-02-02
forum: General Help
---

### Post by kenailes on 2006-02-02
i have a fat32 partition where my media files are stored. I followed the directions and created a new folder in media/windows so that I can mount and write to the folder. I also edited my fstab file. when i mount the drive, I can write to the media/windows folder, but I can't write to the subfolder, specifiacally medi/windows/my music.  what do I need to do in order to get to that part?

thanks for the help. getting closer to being able to drop my windows partition every day

---

### Post by aysiu on 2006-02-02
Can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by kenailes on 2006-02-02
sure  Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2167    17406396    7  HPFS/NTFS
/dev/hda2            2168       10248    64910632+   5  Extended
/dev/hda3           10249       12161    15366172+  83  Linux
/dev/hda5            2168       10162    64219806    b  W95 FAT32
/dev/hda6           10163       10248      690763+  82  Linux swap / Solaris

hda 5 is the one i am trying to access

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              15G  2.3G   12G  17% /
tmpfs                 245M     0  245M   0% /dev/shm
tmpfs                 245M   13M  232M   6% /lib/modules/2.6.12-10-386/volatile
/dev/hda1              17G  5.8G   11G  35% /media/hda1
/dev/hda5              62G   54G  7.4G  89% /media/hda5
/dev/hda5              62G   54G  7.4G  89% /media/windows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/windows  vfat    iocharset=utf8,umask=000       0       0/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
kenny@ubuntu:~$

thanks for the help

---

### Post by aysiu on 2006-02-02
Okay. Please follow these instructions exactly as written, in this exact order. Copy and paste if you don't trust your typing skills: ```
sudo umount /media/windows
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Replace your **entire** file with this instead: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda5 /windows vfat iocharset=utf8,umask=000 0 0
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
``` Then save the file. ```
sudo mount -a
```

---

### Post by kenailes on 2006-02-02
did it exactly as you said, remounted, he windows folder is there, I can open the folder, but then the "my music" folder has to lock over it.  I can access it as root, just not as me...

there are three folders in there--one called my music, one called my pictures, and one call Recordcase which is one i use for my dj job.  i can write to the recordcase folder, but not the other 2

---

### Post by aysiu on 2006-02-02
Darn.

Sometimes the /media/windows thing makes stuff weird, as opposed to just /windows or some other separate folder.

Hm. I'm not sure what the problem could be...

**Edit**: Actually, I just noticed something. You have /dev/hda5 mounted twice, in two different places. Look: ```
/dev/hda5 62G 54G 7.4G 89% /media/hda5
/dev/hda5 62G 54G 7.4G 89% /media/windows
``` You have it mounted at /media/windows *and* at /media/hda5. 

Can you do the following? ```
sudo umount /media/hda5
sudo umount /windows
sudo mount -a
```

---

### Post by akiro.yamamoto on 2006-02-02
EDIT For Content ;)
My FSTAB Entry modify as needed.....
/dev/hda5       /media/windows     vfat    user,umask=000        0       0

My Folders and Files on that Partition 
All have permissions of 777 with root as owner and user even when I create the folder as a regular user.

So I would suggest you remove any duplicate entries in your FSTAB file, forget about isocharset (whatever) and use my entry
as is, just modify it to point to the correct partition and folder.
Then do a:
sudo umount /dev/hda5 
Then:
mount -a 
or simply reboot to ensure everything is mounted properly.
Thanks Aysiu I forgot all about the Fat32 spec. It's been so long since I've used it LOL!
:smile:

---

### Post by aysiu on 2006-02-02
FAT32 doesn't support permissions.
I don't see how *chmod*ing can help...

Maybe I'm wrong.

---

### Post by kenailes on 2006-02-17
sorry didn't realize you guys had been responding again. thanks for the help. i tried the last suggestion and changed my line. my fstab now looks like the following:

 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda5 /windows vfat user,umask=000 0 0
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda2       /mnt/ipod       vfat    rw,user,noauto          0       0


I stil have two folders that are locked...what the heck am i doing wrong?

---

### Post by rowanparker on 2006-02-17
Hi,
I had exactly the same problem with a lock over "My Music" and "My Pictures".
All i did was copy the folder to "Music" and "Pictues" and now its fine.

I know that doesn't solve your problem, but atleast its a tempory solution.

Hope it helps, Rowan.

---

### Post by aysiu on 2006-02-17
[QUOTE=kenailes]
I stil have two folders that are locked...what the heck am i doing wrong?[/QUOTE] Try rebooting your computer.

---

### Post by kenailes on 2006-02-17
hey rowan,

thanks for the suggestion. I have actually thought about doing that, but the problem is if I do that, I haven't fixed the problem, and I am one of those hardheaded people who will keep thinking about it until it gets fixed...

If I don't figure it out, I'll end up going that route.  odd that you had the issue on the exact same two folders...

---

