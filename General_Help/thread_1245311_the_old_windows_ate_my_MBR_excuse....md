---
title: "the old windows ate my MBR excuse..."
date: 2009-08-20
forum: General Help
---

### Post by shiggydiggy on 2009-08-20
howdy peoples!
here's what my HDD looked like this morning ("[]" is a partition, "{}" is extended.)

[20GB NTFS dead WXP]{[large NTFS][/ xfs][swap][/home xfs]}

i've got a jaunty on the xfs.
so i thought i was smart and tried to reinstall windows into that 20GB NTFS... windows didn't want to install even after creating a shiny new partition with windows install. so i said bugger it! i don't need windoze anyway.
now that windows ate my MBR, I fired up the ubuntu live cd, deleted the NTFS and created a small ext2
here's what my HDD looks like now

[empty ext2 1GB][no partition/free space]{[large NTFS][/ xfs][swap][/home xfs]}

I intend on keeping the first 1GB empty because that part of the hdd has been worn out from starting windows every day for 5 years.
To get my MBR all happy like again, I downloaded supergrubdisk and put it on my usb drive. only thing is, it can't see my xfs, so all it could do is put a /boot and all the stuff it does into the little ext2. The only reason I used xfs is because a LFS nerd I know swears by it... I guess i learned something new today lol, don't use xfs...

so, I googled for some solutions...
I found one that said that i could do this ```
sudo grub-install /dev/[your hdd]
```I fired up my jaunty live cd again and did this
```
root@ubuntu:~# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
```talk about doh!
her's another one i found```
sudo grub[INDENT] > root (hd0,0)
 > setup (hd0)
 > exit[/INDENT]
```when i tried that i got```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 
```someone please rescue the noob!
Thanks a lot guys :)

---

### Post by howefield on 2009-08-20
So what's the question ?

---

### Post by shiggydiggy on 2009-08-20
how do I get grub back and configured?

---

### Post by Post Monkeh on 2009-08-20
after you sudo grub, try find /boot/grub/stage1   to make sure you're trying to set up grub on the correct disk.

also, i take it you've got your disks mounted?

---

### Post by shiggydiggy on 2009-08-20
> **Post Monkeh said:**
> after you sudo grub, try find /boot/grub/stage1   to make sure you're trying to set up grub on the correct disk.

also, i take it you've got your disks mounted?
yea, should they be unmounted?
also should't grub install itself on my xfs, and then put an MBR at the start of the hdd?

---

### Post by shiggydiggy on 2009-08-20
here's a guide that fixed it [link](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair)

> Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognize my drive. So I borrowed some knowledge I picked up while using Gentoo:

You have to mount your root partition using the livecd:
Code:

$      Code:
     sudo mkdir /mnt/root 
$      Code:
     sudo mount -t ext3 /dev/sda6 /mnt/root 
Then you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$      Code:
     sudo mount -t proc none /mnt/root/proc 
$      Code:
     sudo mount -o bind /dev /mnt/root/dev 
Doing this allows grub to discover your drives. Next you have to chroot:
Code:

$      Code:
     sudo chroot /mnt/root /bin/bash 
Now that you're chrooted into your drive as root everything should work.
Code:

#      Code:
     sudo grub 
  [COLOR=Red]I edited in the sudo, just to be safe. When I enter grub and not sudo grub, grub cannot find the file. I do not know if the chroot changes this because I did not try it that way. In the end I figured it was better to err on the side of caution. Tosk I hope you don't mind my editing of your reply.[/COLOR]
grub>      Code:
     find /boot/grub/stage1 
It found mine on (hd0,5)
Code:

grub>      Code:
     root (hd0,5) 
It successfully scanned the partition and recognized the filesystem-type
Code:

grub>      Code:
     setup (hd0) 
That was it. It installed and on reboot I was thrown back into Ubuntu.

This might help some people who are having issues so I thought I would post it.

PLEASE NOTE: My Ubuntu was installed to /dev/sda6. This may not be the same for everyone. /dev/sdaX means it's SCSI/SATA/USB/FireWire drive. And it's partition 6 because I have a weird partitioning scheme in place.

--Tosk

i couldn't be bothered typing sudo every time so i did sudo -i :)

---

### Post by Post Monkeh on 2009-08-21
> **shiggydiggy said:**
> yea, should they be unmounted?
also should't grub install itself on my xfs, and then put an MBR at the start of the hdd?

no, they should be mounted.

glad you got it sorted,

---

