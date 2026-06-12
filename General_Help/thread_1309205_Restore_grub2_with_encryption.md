---
title: "Restore grub2 with encryption?"
date: 2009-11-01
forum: General Help
---

### Post by TwiStEr55 on 2009-11-01
Ok, this is a hypothetical. I dont need to restore my grub2 right now, but sometimes I need to (reinstalling windows) and I wanna/need to know this.

For grub it is easy and no problem after doing it often. 
I searched for solutions for grub 2 and all the HowTo's I found involved mounting the linux partition and chrooting into it. Thats not so easy when all there is unencrypted is /boot .. in grub that was enough since all the config files were in /boot

I guess I just answered my own question though. I probably have to start the Live CD and then decrypt the Luks partition and then chroot?

Oh man this is going to be harder since in the encryption is a Lvm.

sda1 /boot
sda2_crypt -> lvm [INDENT][INDENT]1. /
2. swap[/INDENT][/INDENT]

Can anyone help me through this problem? I want to test this on my laptop, so that I dont have to start sweating over my bootsectors when I try to restore grub2 on my production machine.

Thx, Matt

---

### Post by ironfelixx on 2009-12-03
The following steps worked for me with Ubuntu 9.10 (Karmic) x86_64:

launch Ubuntu livecd.
launch terminal

$ sudo apt-get install lvm2
$ sudo fdisk -lu

 (make note of your linux partitions)

$ sudo cryptsetup luksOpen /dev/<your encrypted partition> <some name, say "crypt1">
Enter LUKS passphrase:
key slot 0 unlocked.
Command successful.
$ sudo pvscan
  PV /dev/mapper/crypt1    VG vg_vol1   lvm2 [40.0 GB / 0 free]
$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg_vol1" using metadata type lvm2
$ sudo vgchange -a y
  3 logical volume(s) in volume group "vg_vol1" now active
$ lvscan
ACTIVE       '/dev/vg_vol1/lv_root'
ACTIVE        '/dev/vg_vol1/lv_home'
ACTIVE       '/dev/vg_vol1/lv_swap'
$ sudo mount /dev/vg_vol1/lv_root /mnt

if you have a separate boot partition:
$ sudo mount /dev/<your /boot partition> /mnt/boot

$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
$ sudo chroot /mnt
# grub-install /dev/sda
# grub-install --recheck /dev/sda
# exit
$ sudo umount /mnt/boot
$ sudo umount /mnt
$ sudo reboot

Thanks to the following for the howtos:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)

---

### Post by LENNYMANSELLmansell@gmail on 2010-01-11
THe above procedure works great for me up till the step "grub-install /dev/sda".  My system replies with the message "/dev/mapper/MANE-OF-MY-VOLUME does not have any corresponding BIOS drive."  

Any clues as to what I need to do are appreciated.

Thanks.

---

### Post by meierfra. on 2010-01-11
> "grub-install /dev/sda". 
Skip that step  and continue with the next one:

```
grub-install --recheck /dev/sda". 
```

---

### Post by sanyaldibya on 2010-05-20
I had a similar problem. I have an HP laptop. Recently the internal optical drive (dvd drive) stopped working. I bought an external drive but cannot boot out of it. I have windows vista and lucid on the system. Boot loader is grub2. Thinking that re-installing windows may solve my dvd drive problem I got grub2 wiped out. Then I ended up with vista with no way to boot into ubuntu.
My lucid installation is with lvm. So standard way of recovering grub2 with livecd will not work. Then I found this posting.
I created a bootable usb stick with ubuntu livecd (lucid); used unetbootin for this. I booted into the livecd and exactly used your approach. Worked like a charm! I am back using lucid in 20 mins. Thanks for posting this!

---

### Post by dfaure on 2010-12-28
Thanks for the howto, very useful. Just a note in case it happens to someone else: the chroot command failed for me due to booting a 32bit liveCD on a 64bit system. There's in fact a simpler way to run grub, without the need to chroot:

sudo grub-install --root-directory=/mnt /dev/sda

---

