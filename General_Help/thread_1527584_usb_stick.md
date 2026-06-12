---
title: "usb stick"
date: 2010-07-09
forum: General Help
---

### Post by fidelfloris on 2010-07-09
Good evening,
 
I have Ubuntu on USB.
And I have Ubuntu already installed.
But after installing Ubuntu I installed also windows 7.
Now there is no grub anymore.
 
Can I use my USB stick to mount Ubuntu? And after that, how can I get my grub back?
 
Greetings Floris

---

### Post by cariboo on 2010-07-09
Depending on what version you are running, you can follow the instructions for pre-Karmic [here]("http://ubuntuforums.org/showthread.php?t=224351").

For grub2, boot from the Live CD, once at the desk top open a terminal and type the following:

```
sudo fdisk -l
```

to determine which partition is you Ubuntu / partition. Next:

[list=1]
[*] sudo mount /dev/sda1 /mnt
[*] sudo mount --bind /dev/ mnt/dev
[*] sudo mount --bind /proc /mnt/proc
[*] sudo mount --bind /sys /mnt/sys
[*] sudo chroot /mnt
[/list]

Once yo are at the prompt again type:

```
sudo install-grub /dev/sda
```

then update grub:

```
sudo update-grub
```

Exit chroot:

```
Ctrl-d
```

and reboot.

---

