---
title: "Ubuntu wont start after NTFS config tool"
date: 2010-08-17
forum: General Help
---

### Post by StevenSteavis on 2010-08-17
Hi, I'm new to Linux/Ubuntu. Today I tried to follow some instructions online to mount my windows harddisk so I can read / write from it in Ubuntu. I can't find the website anymore with the tutorial I used. I remember using NTFS configuration tool and enabled write support for internal device, then restarted my system and now I can't get in to ubuntu.

I tried booting up in recovery mode, didn't work. I tried to edit /etc/fstab file but if I want to save it I get the error "Read Only File System".

Now what? :-) How do I solve this?

I have 2 SATA harddisks. On one I have windows XP installed, on the other Ubuntu.

Thx.


Editted to add: I'm running Ubuntu 10.4.1

---

### Post by Lekensteyn on 2010-08-17
You should boot up with your Live CD.
From there, you mount your Ubuntu partition.
That can be done with "sudo mount /dev/sda1 /mnt", replace sda1 with your Ubuntu partition.
You can display all partitions with "sudo fdisk -l"

Have you made any changes to /etc/fstab?
If yes, please post the contents of /etc/fstab ('cat /mnt/etc/fstab' from shell, use Ctrl+Shift+C to copy it)

Ubuntu has built-in support for NTFS drives.
You shouldn't install anything for that.

---

### Post by StevenSteavis on 2010-08-17
Thx for your reply my fellow Dutch man. ;-)

I mounted the Ubuntu partition but that didn't work. I still get the same error during startup (can't see the exact error because it goes away in a blink of an eye).

If I go to computer / filesystem / mnt the directory is empty.

In Filesystem / etc / I do find fstab.

The contents of fstab are:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0


This is different than the contents of fstab when I use 'sudo nano /etc/fstab' command after I get the error during startup in recobery mode.. (I hit S to skip the error, then I get a prompt at which I could write commands).

---

### Post by StevenSteavis on 2010-08-17
maybe this might help, results of sudo fdisk -l:

My windows disk:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24791   199133676    7  HPFS/NTFS

My Linux disk:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19084   153283584   83  Linux
/dev/sdb2           19084       19458     3004417    5  Extended
/dev/sdb5           19084       19458     3004416   82  Linux swap / Solaris

---

### Post by drs305 on 2010-08-17
StevenSteavis, Welcome to the Ubuntu forums. :-)

You should be able to open a terminal and mount your Ubuntu partition with:
```
sudo mount /dev/sdb1 /mnt
gksu gedit /mnt/etc/fstab
```

Copy the contents and post the results here.

It might be useful to also post the contents of the following if your fstab file contains UUIDs (long alphanumeric identifiers):
```
sudo blkid
```

---

### Post by Nervouswreck on 2010-08-17
Could you repaste with the tab stops intact, or post a screenshot?

---

### Post by StevenSteavis on 2010-08-17
contents of /mnt/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /    ntfs-3g    defaults,locale=en_US.utf8    0    0
/dev/sda5    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0


I guess the problem must be in the /dev/sda1 line somewhere..(but I'm a newby so I might be totally wrong!) because when starting up ubuntu I very quickly see an error that is something along the lines of: 'unrecognised mount option "locale=english/US" etc.. can't see the rest of the error as it's too fast. 


contents of sudo blkid:

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="WindowsXP" UUID="DE80A1CE80A1AE09" TYPE="ntfs" 
/dev/sdb1: UUID="66736d79-0d88-42b8-9506-6b3e98cc3875" TYPE="ext4" 
/dev/sdb5: UUID="d75a512e-e9b4-4542-8521-8bebf1d2295c" TYPE="swap" 


Thx for the replies and help guys. I appreciate it.

---

### Post by drs305 on 2010-08-17
Actually, the problem is that your fstab entry doesn't include the linux installation. *If* it exists in /dev/sdb1, add this line to /mnt/etc/fstab:

> 
UUID=66736d79-0d88-42b8-9506-6b3e98cc3875 /  ext4    errors=remount-ro  0 1

Also, you swap is listed as "sda5" but should be **sdb5** according to what you've posted.
> /dev/**sda5 **none swap sw 0 0

Save the file, then try rebooting without the LiveCD inserted.

---

### Post by StevenSteavis on 2010-08-17
drs305, you're the MAN! Adding "UUID=66736d79-0d88-42b8-9506-6b3e98cc3875 / ext4 errors=remount-ro 0 1" to the fstab file fixed everything. I'm back into Ubuntu.. and this time not the Live CD. Thanks a lot!!! :guitar:

I just changed /dev/sda5 to /dev/sdb5. Going to reboot again.

Now.. how can I mount the drive which has windows located on it so I can access it from ubuntu? Same counts for the 2nd partition on the HD which has Linux on it (Linux is located on first partition, second partition is empty for now). I noticed when using the Live CD I saw these drives under 'Computer'.. but when ubuntu is installed on the HD these drives are not there.

---

### Post by StevenSteavis on 2010-08-17
For what it's worth, in Disk Utility I saw that my hard disk which has windows on it says Mount Point: Not Mounted. When I click 'Mount Volume' I get this error:
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

---

### Post by Cavsfan on 2010-08-17
**drs305** is indeed the man when it comes to GRUB2 whether it's fixing it after a windows install or really anything.
He knows quite a lot about this stuff!

I just thought that after you get every thing fixed and since you are dual booting, you might want to take a look 
at my tutorial in my signature. It really makes GRUB2 maintenance free. My tutorial is even mentioned at the 
bottom of **drs305** GRUB2 tutorial with everything you would ever want to know about it!

---

### Post by tripmix on 2010-08-17
You can manually mount it like this
```
sudo mount -t ntfs-3g /dev/sda1 /anywhere/you/want
```
or to make it mount at boot add this
```
/dev/sda1 /anywhere/you/want ntfs-3g defaults 0 0
```
to /etc/fstab

---

### Post by drs305 on 2010-08-17
Remove this, as it is incorrect:
> /dev/sda1 / ntfs-3g defaults,locale=en_US.utf8 0 0


Your sda1 (Windows) entry in fstab, if you would like to mount it via fstab, should read:
> UUID=DE80A1CE80A1AE09 /media/windows ntfs-3g defaults,umask=002,uid=1000,gid=1000,locale=en_US.utf8 0 0

You will need to make the mount point. If you don't want the /media/windows, change this entry and the fstab entry:
```
sudo mkdir /media/windows
sudo chown -R <yourusername>: /media/windows
```
Example:
sudo chown -R john: /media/windows

The *umask* entry is personal preference. It sets permissions for you and others. *002* is fairly liberal. You can search "fstab" and "umask" to see what various settings will do.

---

### Post by StevenSteavis on 2010-08-18
Thx again drs305!! All is working great now. I have ubuntu up and running how I want it to... and it's kicking Windows' ***!

---

