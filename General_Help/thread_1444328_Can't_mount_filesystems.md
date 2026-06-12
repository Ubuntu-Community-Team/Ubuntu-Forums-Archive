---
title: "Can't mount filesystems"
date: 2010-04-01
forum: General Help
---

### Post by FrenchyFungus on 2010-04-01
This morning when I booted my laptop I received a bash screen which said "General error mounting filesystems".

I thought it may have been a GRUB problem, so booted from a Live CD and tried to update grub using sudo update-grub, It gave me the error "grub-probe error cannot find a device for /.".

I then tried this: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) and now when I boot my laptop I get a grub screen.

Not wanting to **** things up further, I thought I'd ask if anyone knows how to fix this.

Cheers.

---

### Post by m4tic on 2010-04-01
using live cd
the X is your partition number which you can find by
```
sudo fdisk -l
```
 
```
[FONT=Courier New]$sudo mount /dev/sdaX /mnt
$sudo mount --bind /dev /mnt/dev[/FONT]
$sudo mount --bind /proc /mnt/proc
[FONT=Courier New]sudo chroot /mnt[/FONT]
[FONT=Courier New]#grub-install --recheck /dev/sda[/FONT]

[FONT=Courier New]$sudo reboot[/FONT] 

```

---

### Post by FrenchyFungus on 2010-04-01
Cheers. However, sudo mount --bind /proc /mnt/proc gives the error message "mount: /proc: can't read superblock"

---

### Post by m4tic on 2010-04-01
e2fsck -f -y -v /dev/sdaX

---

### Post by FrenchyFungus on 2010-04-01
Fantastic, it's working fine now.

In the interests of preventing it from happening again, do you know why this happened?

Many thanks.

---

