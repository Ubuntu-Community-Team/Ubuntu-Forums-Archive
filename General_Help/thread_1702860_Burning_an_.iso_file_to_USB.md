---
title: "Burning an .iso file to USB"
date: 2011-03-08
forum: General Help
---

### Post by Jonker on 2011-03-08
Hi there,
I would like to burn this iso ([http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)) to a 2GB USB drive. All the instructions which I found were for ubuntu installations on a USB, but there was no general way.

---

### Post by Verbeck on 2011-03-08
i guess the method for windows installations disks would work here

1. open gparted (install it if you don't have) and format the usb stick as ntfs 
2. right click the partition > manage flags > check 'boot'
3. extract the contents of the iso to the usb disk

hope that does it..

---

### Post by lithopsian on 2011-03-08
A fairly generic way to "burn" an ISO image on a USB is to use the Linux dd command.

---

### Post by dandnsmith on 2011-03-08
> **lithopsian said:**
> A fairly generic way to "burn" an ISO image on a USB is to use the Linux dd command.

I'd go with that - no way would I format the stick NTFS, unless faced with overwhelming reason so to do.

---

### Post by Verbeck on 2011-03-08
iirc, windows vista/7 iso's create a ntfs partition (and destroys the existing partition table) when used with dd
which results in more or less the same thing

---

### Post by Jonker on 2011-03-08
thanks, how do you use the dd command?
My USb is /dev/sdc an currently formated in FAT16. The Iso image is on my desktop.
Because I'm not (yet) very good in the terminal, I would appreciate a code( If thats possible). 
 PS: I am using Ubuntu 10.10

---

### Post by Verbeck on 2011-03-08
the command would be like 
```
sudo dd if=/path/to/iso/file.iso of=/dev/sdX
```where /dev/sdX would be your device
run *sudo fdisk -l *if you're unsure of the device name

(remember to backup any files on the stick before you do that)

---

### Post by Jonker on 2011-03-08
hi,
the dd didnt work, so I tried the first way (by Verbeck)  and it worked. Thanks allot for your help!!!):P

---

