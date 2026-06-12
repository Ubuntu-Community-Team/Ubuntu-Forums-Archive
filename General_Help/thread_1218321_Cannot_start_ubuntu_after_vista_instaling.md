---
title: "Cannot start ubuntu after vista instaling"
date: 2009-07-20
forum: General Help
---

### Post by miros84 on 2009-07-20
Hi.
I have a computer. 1 hdd. In disk management I have the particion in this order

1. Windows Vista
2. Ubuntu
3. Swap for ubuntu
4. Windows xp

My MBR is just now with windows vista loader, but with easyBCD I added NeoGrub as it´s described [here]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4")

So, when I star my computer I can choose 
-windows vista
-windows xp
-grub loader

And when I enter in grub loader, I have
-Ubuntu 9.04
-Ubuntu recovery
-Mem Test

But when I want to enter in Ubuntu 9.04 I recived

error 17: file not found

I can enter in windows vista, start again easyBCD, star neogrub and modify it, but I don´t know how to do it. I tried several times and no one was good.
I tried theese ones:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3d1123c6-40d6-4364-af72-e558686ee739
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d1123c6-40d6-4364-af72-e558686ee739 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3d1123c6-40d6-4364-af72-e558686ee739
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d1123c6-40d6-4364-af72-e558686ee739 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3d1123c6-40d6-4364-af72-e558686ee739
kernel        /boot/memtest86+.bin
quiet

title         Ubuntu  try1
root          (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d1123c6-40d6-4364-af72-e558686ee739 ro  single

title         Ubuntu  try2
root          (hd0,2)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d1123c6-40d6-4364-af72-e558686ee739 ro  single

title         Ubuntu try3
root          (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/hda1 ro

title         Ubuntu try4
root          (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/hda2 ro


Please help me modify correctly my boot list and start again my ubuntu.
As I seid before, I have only 1 hard drive with 4 partitions.
1.Vista
2.Ubuntu
3.Swap
4.XP

---

### Post by kogger on 2009-07-20
If Ubuntu is your second partition, the root will be (hd0,1).

Try going into grub, typing 'c' to go into command-line mode, and typing this in:

```
kernel /vmlinuz root=/dev/sda2
boot
```

---

### Post by miros84 on 2009-07-20
I tried it, but doesnot work. Somebody know how can I do it?

---

### Post by merlinus on 2009-07-20
Try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

If that does not boot ubuntu, then post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

