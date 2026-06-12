---
title: "Urgent problem with grub"
date: 2010-02-26
forum: General Help
---

### Post by motorhead_1 on 2010-02-26
I ve tried to install win xp in a ntfs partition but something went wrong and now I can t lunch ubuntu since there are problems with the grub. could someone help me out step by step in order to recover ubuntu

i m using the live cd right now

---

### Post by ABCC on 2010-02-26
Here's the basic idea, assuming you're using Karmic and thus grub2 (aka 1.97...):

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

hth,

ABCC

---

### Post by motorhead_1 on 2010-02-26
should I follow this guide even in the case that the win installation hasn t been completed

---

### Post by motorhead_1 on 2010-02-26
ubuntu@ubuntu:~$ $sudo mount /dev/sda1 /mnt
mount: only root can do that
ubuntu@ubuntu:~$ 


how do I gain this access

---

### Post by motorhead_1 on 2010-02-26
thats my table right now

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf6d9322

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1890    15181393+   7  HPFS/NTFS
/dev/sda2            1891        9547    61504852+  83  Linux
/dev/sda3            9548        9729     1461915    5  Extended
/dev/sda5            9548        9729     1461883+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by motorhead_1 on 2010-02-26
I dont understand why I don t get root acess despite the sudo command...

---

### Post by tacantara on 2010-02-26
> **motorhead_1 said:**
> ubuntu@ubuntu:~$ $sudo mount /dev/sda1 /mnt
mount: only root can do that
ubuntu@ubuntu:~$ 


how do I gain this access

You've added an extra $ where you don't need it, so the sudo command isn't being recognized.  Try this out:

```
sudo mount /dev/sda1 /mnt
```

You should be able to copy/paste the code into your terminal, or type it verbatim as it appears in the code box.

---

### Post by ABCC on 2010-02-26
Whether or not you fix grub now is up to you, if you decide to install windows again some other time you'll have to reinstall grub also to make ubuntu bootable again.

Anyway, heres an slightly edited version of the blog linked, I'm going to assume that you've installed ubuntu on /dev/sda2.

```

sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
grub-install /dev/sda

#exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

```

I can't recall if you can sudo on the live cd, you could try 'sudo -i' (after which you wont need to prepend commands with sudo).

---

### Post by ABCC on 2010-02-26
> **tacantara said:**
> You've added an extra $ where you don't need it, so the sudo command isn't being recognized.  Try this out:

```
sudo mount /dev/sda1 /mnt
```

You should be able to copy/paste the code into your terminal, or type it verbatim as it appears in the code box.

Well spotted :D

---

### Post by motorhead_1 on 2010-02-26
> **ABCC said:**
> Whether or not you fix grub now is up to you, if you decide to install windows again some other time you'll have to reinstall grub also to make ubuntu bootable again.

Anyway, heres an slightly edited version of the blog linked, I'm going to assume that you've installed ubuntu on /dev/sda2.

```

sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
grub-install /dev/sda

```this my input after this part 

Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
root@ubuntu:/# 

> **ABCC said:**
> 

```


#exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

```
do I copy paste this part now 


I m sorry but I can find the question mark with the live cd qwery layout

---

### Post by motorhead_1 on 2010-02-26
(hd0)    /dev/sda
root@ubuntu:/# #exit
root@ubuntu:/# sudo umount /mnt/dev
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo umount /mnt/proc
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo umount /mnt
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo reboot

---

### Post by ABCC on 2010-02-26
Sure you can copy that as is, it's simply tidyies up the environment and reboots.

---

### Post by motorhead_1 on 2010-02-26
*edit*

---

### Post by motorhead_1 on 2010-02-26
edit

---

### Post by motorhead_1 on 2010-02-26
edit: solved thank you ABCC!

---

### Post by motorhead_1 on 2010-02-27
edit

---

