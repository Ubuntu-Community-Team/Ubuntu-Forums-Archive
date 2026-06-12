---
title: "How to gain acces to other Linux Disk"
date: 2010-07-02
forum: General Help
---

### Post by ExpL0it0R on 2010-07-02
Hi. How can i gain access to write/read/execute to my Ubuntu disk if i use live CD ?

---

### Post by sdowney717 on 2010-07-02
you have to 'chroot' yourself into the os. This is related to mounting the disk when running the live cd.

> (4) From the Live Desktop run:

Code:

sudo mount /dev/sdXY /mnt

(of course XY must represent your drive and partition #'s!)

Then:

Code:

sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

You should notice that the command prompt changes from ubuntu@ubuntu$ to # which means you're now root in that OS. I like to be sure I am where I want to be with "cat /etc/issue" and "df -H".

Then revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

And when you're done:

Code:

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt

---

### Post by ExpL0it0R on 2010-07-02
Thanks..!

---

### Post by duncan303 on 2010-07-02
This is exactly what I would like to achieve.
boot the cd, 
go to system>admin>diskutility and find the device name  of the ubuntu installation (in my case sda5) so in the terminal I type


ubuntu@ubuntu:~$ sudo mount /dev/sda5/mnt

and the reply is
mount: can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab

however I can mount the media in nautilus mount point being /media/linux drive

 and fstab and mtab are there.

this is the content of fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e8e0b6bb-c9f5-449c-915f-a6c1fab98277 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=2cc76a19-a947-4444-b475-ff026c208de2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
 So if it not sda5 ......... where is it??
thnks if anyone can help

---

### Post by oldos2er on 2010-07-02
> **duncan303 said:**
> ubuntu@ubuntu:~$ sudo mount /dev/sda5/mnt

and the reply is
mount: can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab


There should be a space inbetween /dev/sda5 and /mnt
```
sudo mount /dev/sda5 /mnt
```
This assumes the mount point /mnt already exists. If it doesn't, you'll need to create it ```
sudo mkdir /mnt
```

---

### Post by duncan303 on 2010-07-02
many thanks, i got that, and it mounts, but chroot fails because...........

 now it appears as if I am using the wrong livecd10.4 32bit and therefore I need to find a machine to download and burn a new cd. I upgraded online so I have to create a 10.4 in 64bit livecd


Many thanks for helping

cheers..

---

### Post by duncan303 on 2010-07-03
I was helped in another post, and discovered that I did not need to use a livecd specific to the installation if i used the simple command from the livecd  terminal

```
gksu nautilus
```this worked perfectly for me.

thanks for help

---

