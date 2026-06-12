---
title: "Hard drive: Read only problem"
date: 2011-12-25
forum: General Help
---

### Post by AaronDaycentChild on 2011-12-25
I'm trying to create a backup of all my files on an external hard drive but every time I try I get an error message saying that it's a "Read Only File System". I've tried re-formatting to NTFS and changing the permissions but none of it seems to be working.. 

Anyone know anything about this?

---

### Post by Synoc on 2011-12-25
first, I would not use NTFS for an external drive. It's not a Linux native file system. I would keep it as a FAT 32, for maximum portability if if it ONLY going to be used to Linux, and you want File permissions, then I'd go with ext4. 

I DO find it odd that it is mounting as Read-only. if this is a USB it SHOULD automount as read write.

For now if this continues, use 
```
sudo mount -t fat32 -o rw /dev/sdb1 /mnt
```
This assumes a fat32 file system and that your drive is the second hard drive connected to the computer, AND that you want to use the first/only partition on that drive. 

This also means you may have to use type ```
sudo nautilus
```
to back up said files. as it will mount the hard drive for the root user, but that should do it. if you code post us the output of ```
cat /etc/fstab
```that would tell us if there is anything "wonky" with your file system mounting procedure

"Wonky" is an industry term

---

### Post by fdrake on 2011-12-25
fat32 has a file-syze limit of 4GB which is pretty annoyng nowadays if you have dvd-iso's. If you don't then that's fine! Unfortunately nowadays you cannot make happy everyone MacOS/Win/*nix. If you are working between win and *nix, NTFS is a good choice in my opinion (for the reason stated above). If you are working with MacOS then you can you HFS (no journal!!!). Fat32 it will work on all well if you don't have files >=4gb

---

### Post by AaronDaycentChild on 2011-12-25
> **Synoc said:**
> first, I would not use NTFS for an external drive. It's not a Linux native file system. I would keep it as a FAT 32, for maximum portability if if it ONLY going to be used to Linux, and you want File permissions, then I'd go with ext4. 

I DO find it odd that it is mounting as Read-only. if this is a USB it SHOULD automount as read write.

For now if this continues, use 
```
sudo mount -t fat32 -o rw /dev/sdb1 /mnt
```
This assumes a fat32 file system and that your drive is the second hard drive connected to the computer, AND that you want to use the first/only partition on that drive. 

This also means you may have to use type ```
sudo nautilus
```
to back up said files. as it will mount the hard drive for the root user, but that should do it. if you code post us the output of ```
cat /etc/fstab
```that would tell us if there is anything "wonky" with your file system mounting procedure

"Wonky" is an industry term

This code didn't work for some reason:
```
sudo mount -t fat32 -o rw /dev/sdb1 /mnt
```

Instead I got this read out:
```
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?
```

For ```
cat /etc/fstab
``` I got this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

```

The external drive doesn't seem to register.

---

### Post by fdrake on 2011-12-25
the type is wrong , ot should be:
```

sudo mount -t vfat /dev/sdb1 /mnt

```

---

### Post by AaronDaycentChild on 2011-12-25
> **fdrake said:**
> fat32 has a file-syze limit of 4GB which is pretty annoyng nowadays if you have dvd-iso's. If you don't then that's fine! Unfortunately nowadays you cannot make happy everyone MacOS/Win/*nix. If you are working between win and *nix, NTFS is a good choice in my opinion (for the reason stated above). If you are working with MacOS then you can you HFS (no journal!!!). Fat32 it will work on all well if you don't have files >=4gb

Ah I see. 

I can't put ANY amount of files from my computer to my hard drive. I don't get it..

---

### Post by fdrake on 2011-12-25
> **AaronDaycentChild said:**
> Ah I see. 

I can't put ANY amount of files from my computer to my hard drive. I don't get it..

no you can put files in the fat32 system but the files cannot be bigger that 4GB in size. let's say you have a *.rar or *.zip file . The cannot be bigger then 4GB otherwise the copying process won't be successful!
see [http://wiki.vuze.com/w/FAT32_file_size_limit](http://wiki.vuze.com/w/FAT32_file_size_limit)

hold a moment are you mounting a FAT32 or NTFS disk?

---

### Post by AaronDaycentChild on 2011-12-25
> **fdrake said:**
> no you can put files in the fat32 system but the files cannot be bigger that 4GB in size. let's say you have a *.rar or *.zip file . The cannot be bigger then 4GB otherwise the copying process won't be successful!
see [http://wiki.vuze.com/w/FAT32_file_size_limit](http://wiki.vuze.com/w/FAT32_file_size_limit)

Oh, I see now. Thank you!

> **Synoc said:**
> first, I would not use NTFS for an external drive. It's not a Linux native file system. I would keep it as a FAT 32, for maximum portability if if it ONLY going to be used to Linux, and you want File permissions, then I'd go with ext4. 

I DO find it odd that it is mounting as Read-only. if this is a USB it SHOULD automount as read write.

For now if this continues, use 
```
sudo mount -t fat32 -o rw /dev/sdb1 /mnt
```
This assumes a fat32 file system and that your drive is the second hard drive connected to the computer, AND that you want to use the first/only partition on that drive. 

This also means you may have to use type ```
sudo nautilus
```
to back up said files. as it will mount the hard drive for the root user, but that should do it. if you code post us the output of ```
cat /etc/fstab
```that would tell us if there is anything "wonky" with your file system mounting procedure

"Wonky" is an industry term

Okay, I got it working. It's finally backing up. No problems yet. 

Just one question: If I quit the terminal will the process cancel?

---

### Post by fdrake on 2011-12-25
to mount ntfs do:
```

sudo apt-get install  ntfs-3g ntfs-config
sudo reboot now
sudo mkdir /media/ntfs
sudo mount -t vfuse /dev/sdb1 /media/ntfs

```

---

### Post by Synoc on 2011-12-25
exiting terminal will have no effect on your mounted file systems. BTW sorry about the code, been a while... the /etc/fstab file will not show any drives connected to the... What it does show is how the permenantly mounted file systems are mounted. If you want this new hard drive to permanently mount, you add it to this file. if you want to mount it as needed, then "sudo mount" will work. That said.  IS this a USB HHD? and if so, haave you been able to get it to automount?

PS sorry about the mount syntax, I am rusty on manually mounting a fat system.

---

### Post by motoso on 2011-12-26
I would like to keep my NTFS external hard drive for now. Maybe I'll format to FAT32 later, but I don't have time right now.
If I mount it using fdrake's solution, will it become read-write every time I plug it in?

I read somewhere else I can use

```
cd /media/your_external_drive 
sudo chmod -R 777 *
```

Will this allow me to permanently read/write on this drive?

---

### Post by Synoc on 2011-12-27
the default to mount an external drive in ubuntu is read/write chmod won't affect that. the -R flag will tell chmod to change the permissions for files/folders inside the directory you are working in, recursively, meaning everything inside. however new files will be rw-r--r-- but I don't think NTFS honors linux permissions. I could be wrong. 

when you mount or auto mount a drive however it should default to r/w. the only way to permanently mount the drive however is to add it to the /etc/fstab file. then it will mount on startup. If you WANT to mount it only on a as needed basis, then just use the mount command. 

BTW the code you typed... setting the octal permissions to 777 means YOU can read/write/execute, anyone in your group can as well... and so can the rest of the world. the only thing I see with 777 permissions are sim links. it is as insecure practice

---

### Post by fdrake on 2011-12-27
> **motoso said:**
> 
```
cd /media/your_external_drive 
sudo chmod -R 777 *
```

Will this allow me to permanently read/write on this drive?

you access ntfs trougth the FUSE virtual filesystem. All the permissions bits assigned to the files/inodes are virtual (specific to the Fuse driver!). If you change the permissions and plug the drive to another sys using FUSE driver the permissions maybe respected, if the sys does not use fuse (like windows, {note that other drivers do exist}), well then the permissions won't be respected. 
In the end the permissions are assigned virtually and are strictly dependable from the driver that you use.... that's my general opinion. :D

---

### Post by motoso on 2011-12-27
Thanks fdrake, I installed the program, and rebooted. I didn't even have to mount manually, and it works. Now my drive is read/write.

---

