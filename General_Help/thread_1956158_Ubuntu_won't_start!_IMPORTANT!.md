---
title: "Ubuntu won't start! IMPORTANT!"
date: 2012-04-10
forum: General Help
---

### Post by dg1598 on 2012-04-10
I installed Ubuntu 11.10 through Wubi because I can't run my server with more than 1gb of RAM off windows since its 32bit. Anyway, I came home from school and my desktop was 100% frozen, the mouse didn't even move. I held down my power button until the laptop turned off, and restarted it, at the selection screen I chose Ubuntu and it now gets stuck at a purple screen. I don't necessarily want Ubuntu repaired, just a way to access my desktop to retrieve a my server folder. Really need help with this because the server is my only source of income! Thanks a lot,
-D

---

### Post by alex2e1gzy on 2012-04-10
Maybe try a Live CD to recover your folder? You can boot in, mount your Ubuntu partition and recover the data. Then you can look at what is causing the problem...

---

### Post by roelforg on 2012-04-10
You shouldn't use wubi for important systems, you should multiboot.

Also,
linux is never really frozen (unlike windows).
Unless you can actually get it to swap all the time, it's savable.
Press the keys R+E+I+S+U+B slowly and long whilst holding the sysrq (usually alt+sysrq on desktops)
This tells the kernel to take control and force the most critical shutdown steps before B reboots.
Believe it or not, this actually produces a clean reboot as long as the keyboard isn't physically broken.

---

### Post by roelforg on 2012-04-10
> **alex2e1gzy said:**
> Maybe try a Live CD to recover your folder? You can boot in, mount your Ubuntu partition and recover the data. Then you can look at what is causing the problem...

He said wubi,
so i suspect the wubi rootfs got corrupted as it's really sensitive to hard-reboots.

---

### Post by dg1598 on 2012-04-10
> **alex2e1gzy said:**
> Maybe try a Live CD to recover your folder? You can boot in, mount your Ubuntu partition and recover the data. Then you can look at what is causing the problem...

Like the Ubuntu CD I have? When I do that it either says "Try Ubuntu" or "Install along side windows, or as your only operation system" or something along those lines anyway.. Would you be able to tell me what I would need to do to mount my ubuntu partition? I believe it is under /ubuntu/disks/root.disk  I think thats it anyway :/

---

### Post by dg1598 on 2012-04-10
> **roelforg said:**
> You shouldn't use wubi for important systems, you should multiboot.

Also,
linux is never really frozen (unlike windows).
Unless you can actually get it to swap all the time, it's savable.
Press the keys R+E+I+S+U+B slowly and long whilst holding the sysrq (usually alt+sysrq on desktops)
This tells the kernel to take control and force the most critical shutdown steps before B reboots.
Believe it or not, this actually produces a clean reboot as long as the keyboard isn't physically broken.

I was unaware of this, thanks, so just hold all of them for a while while holding SysRq?

---

### Post by coffeecat on 2012-04-10
> **dg1598 said:**
> Like the Ubuntu CD I have? When I do that it either says "Try Ubuntu" or "Install along side windows, or as your only operation system" or something along those lines anyway.. Would you be able to tell me what I would need to do to mount my ubuntu partition? I believe it is under /ubuntu/disks/root.disk  I think thats it anyway :/

How to mount and/or repair the filesystem in a wubi system:

[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)

---

### Post by roelforg on 2012-04-10
> **dg1598 said:**
> I was unaware of this, thanks, so just hold all of them for a while while holding SysRq?

Assuming your kbd's sysrq is alt+sysrq,
one after oneother, hold each sysrq+key for 5sec, and then release.
Works on every linux as it's in the kernel itself.

---

### Post by dg1598 on 2012-04-10
> **coffeecat said:**
> How to mount and/or repair the filesystem in a wubi system:

[https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F](https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F)
 
I have seen that guide and tried to follow it but I don't quite understand the "replace sda1 part with..." etc. and also when booted from the disk, and tried sudo mkdir /win   i got something like this couldn't be found or this already exists, one of the two. Also is there anyway to mount it on windows? All I want to do is take one folder from it.

---

### Post by dg1598 on 2012-04-10
> **roelforg said:**
> Assuming your kbd's sysrq is alt+sysrq,
one after oneother, hold each sysrq+key for 5sec, and then release.
Works on every linux as it's in the kernel itself.
Thanks for the information but I'll only be able to put this into practice if I get Ubuntu back again.. I don't mind losing ANYTHING on the Partition apart from a folder named "server" on my Desktop.

---

### Post by jwbrase on 2012-04-10
> **roelforg said:**
> You shouldn't use wubi for important systems, you should multiboot.

Also,
linux is never really frozen (unlike windows).
Unless you can actually get it to swap all the time, it's savable.
Press the keys R+E+I+S+U+B slowly and long whilst holding the sysrq (usually alt+sysrq on desktops)
This tells the kernel to take control and force the most critical shutdown steps before B reboots.
Believe it or not, this actually produces a clean reboot as long as the keyboard isn't physically broken.

I have had my machine not respond to REISUB before. It's rare, but it does happen.

---

### Post by alex2e1gzy on 2012-04-10
> **dg1598 said:**
> I have seen that guide and tried to follow it but I don't quite understand the "replace sda1 part with..." etc. and also when booted from the disk, and tried sudo mkdir /win   i got something like this couldn't be found or this already exists, one of the two. Also is there anyway to mount it on windows? All I want to do is take one folder from it.

After selecting 'Try Ubuntu' from the Live CD, open a terminal and type 
```
sudo fdisk -l
```Which will tell you where your Windows Partition is located. Most likely sda1.

---

### Post by dg1598 on 2012-04-10
> **alex2e1gzy said:**
> After selecting 'Try Ubuntu' from the Live CD, open a terminal and type 
```
sudo fdisk -l
```Which will tell you where your Windows Partition is located. Most likely sda1.

Thanks, I'll give it a go. The code I have written down is the following 

sudo mkdir /win
sudo mount /dev/(sda..?)/win
sudo mkdir /vdisk 
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
sudo fsck /win/ubuntu/disks/root.disk 

Is this all correct? :confused:

---

### Post by dg1598 on 2012-04-10
I get this.. (Copied straight from terminal)
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x499a1b85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   420341759   210067456    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo mkridr /win
sudo: mkridr: command not found
ubuntu@ubuntu:~$ sudo mkdir /win
mkdir: cannot create directory `/win': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda2/win
mount: can't find /dev/sda2/win in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$

---

### Post by roelforg on 2012-04-10
> **dg1598 said:**
> I get this.. (Copied straight from terminal)
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x499a1b85

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   420341759   210067456    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ sudo mkridr /win
sudo: mkridr: command not found
ubuntu@ubuntu:~$ sudo mkdir /win
mkdir: cannot create directory `/win': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda2/win
mount: can't find /dev/sda2/win in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$
```

sudo mount /dev/sda2 /win

```
you forgot sudo and a space

---

### Post by dg1598 on 2012-04-10
> **roelforg said:**
> ```

sudo mount /dev/sda2 /win

```you forgot sudo and a space

Ah a space, thanks!

---

### Post by dg1598 on 2012-04-10
Nope, no good..

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

---

### Post by alex2e1gzy on 2012-04-10
I have heard this may be due to Windows not releasing the volume on shutdown. I suggest you reboot into Windows, then Shutdown again.

---

### Post by dg1598 on 2012-04-10
> **alex2e1gzy said:**
> I have heard this may be due to Windows not releasing the volume on shutdown. I suggest you reboot into Windows, then Shutdown again.

I'll try that, I also read it is something to do with not having NTFS-3G?

---

### Post by roelforg on 2012-04-10
> **dg1598 said:**
> Nope, no good..

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /win
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

run:
```

sudo umount /dev/sda2
sudo mount /dev/sda2 /win

```

---

### Post by dg1598 on 2012-04-10
Ok, I think I got it right now, I did a file check and now this is the last message I got. Is this good or bad? I'm gonna try and boot Ubuntu again now.

---

### Post by roelforg on 2012-04-10
> **dg1598 said:**
> Ok, I think I got it right now, I did a file check and now this is the last message I got. Is this good or bad? I'm gonna try and boot Ubuntu again now.

What message?

Iirc, wubi keeps the rootfs as raw hd-image.
If you can find it you can do:
```

sudo mkdir /media/ubuntu
sudo mount /path/to/rootfs.img /media/ubuntu
#...copy your files...
sudo umount /media/ubuntu

```

---

### Post by dg1598 on 2012-04-10
Forgot to paste the message in, but the good news is it booted up! Thanks God! It said something like "Filesystem checked, there are still some errors" so I restarted it and ubuntu did another check itself and now its working perfect! Thanks a lot to the 4 (I think) that replied to this post!

---

### Post by roelforg on 2012-04-10
> **dg1598 said:**
> Forgot to paste the message in, but the good news is it booted up! Thanks God! It said something like "Filesystem checked, there are still some errors" so I restarted it and ubuntu did another check itself and now its working perfect! Thanks a lot to the 4 (I think) that replied to this post!

e2fsck is one of the better designed fsck progs, fixes a lot!
Though the reiserfs fsck even fixed a totally corrupt one... (that one gets a lot of testing because reiser itself is buggy)


Anyhow, please consider giving ubuntu it's own partition.
At least it works ;)

---

