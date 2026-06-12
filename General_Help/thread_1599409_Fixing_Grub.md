---
title: "Fixing Grub"
date: 2010-10-17
forum: General Help
---

### Post by Shadow21 on 2010-10-17
I setup my new Netbook with Windows, Ubuntu, and BackTrack and grub messed up after I installed BackTrack because BackTrack took control of grub and wouldn't let me boot into Ubuntu anymore. I went through the same steps (that I used on my desktop) to reinstall grub on the Ubuntu partition but when I tried to reboot my computer it booted into the grub shell.

I used the commands:
 
```
sudo mount /dev/sdb3 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sdb
```when I was installing grub from the livecd because my hard drive is on sdb and my Ubuntu partition is on sdb3. This is what it said after I ran the install command:

```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
Installing GRUB to /dev/sdb as (hd1)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

How can I fix grub?

I attached the bootinfo results for my Netbook.

---

