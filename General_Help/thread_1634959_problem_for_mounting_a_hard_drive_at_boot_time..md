---
title: "problem for mounting a hard drive at boot time."
date: 2010-12-01
forum: General Help
---

### Post by erogol on 2010-12-01
I used Storage DEvice Management program to set the start up booted hard drives but when I start the computer UBUNTU says "an error occured when booting sda3" but if I skip this process there is no problem while accessing it. Do you know the reason of this message and can you help for the solution ? 

Thanks...

---

### Post by dino99 on 2010-12-01
/etc/fstab might have a wrong config for that partition (check it)

sudo dpkg-reconfigure mountall

---

### Post by Crazedpsyc on 2010-12-01
Do you know the format in /etc/fstab? That is probably where you should try mounting your device from.
Here is an example:
> /host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1and explanation:
Because I installed ubuntu with wubi my filesystem is actually in /host/ubuntu/dists/root.disk, but you should use /dev/sda3 (if that is actually the device) (try looking for your device in System>Administration>Disk Utility to find the device name [will be /dev/something])
/ is the location for the device to be mounted. you can use /mnt or /media/emptyfolder for this.
ext4 is the filesystem type. That can also be found in the Disk Utility program, and if it was designed for windows and you haven't reformatted it it is most likely fat32 for backup drive or ntfs for extra boot device.
the next part just tells the system to retry mounting the device if it fails the first time, and this part should be left out unless you will try to boot from the device. it is only there because if it cannot mount the root filesystem there is no point in doing anything else.
So just press Alt+F2 and enter "gksudo gedit /etc/fstab" to add your device in this format.


Hope you find this helpful!

---

### Post by tajiknomi on 2010-12-01
[SIZE=2]The following link will help you to manage your fstab >[/SIZE][http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

