---
title: "Restoring GRUB"
date: 2010-02-28
forum: General Help
---

### Post by EPurpl3 on 2010-02-28
Hello, 
i have reinstalled windows and the grub does not work any more so i have to reinstall grub manually.I have done this a long time ago and everything went wrong so i want to ask a expert first. 
I dont know what partition holds the boot directory, last time i have specified > hd(0,0) and i was unable to boot windows. When i type ```
grub> find /boot/grub/stage1
``` it says > (hd0,5), in a tutorial it says i should use > hd(0,0), does ubuntu installs grub on > hd(0,0) automaticaly? My computer has (when i look into GParted):

> sda1 - NTFS
sda2 - extended
sda5 - NTFS
sda6 - ext3
sda7 - linux-swap

So where should i install Linux without destroying Windows? > (hd0,5) or > (hd0,0)?

Thanks.

P.S. I have installed Ubuntu Hardy.

---

### Post by EPurpl3 on 2010-02-28
Anybody? Is such a hard question? xD

---

### Post by -Robert- on 2010-02-28
[QUOTE=EPurpl3]So where should i install Linux without destroying Windows? [/QUOTE]

You're not installing Linux/Ubuntu but you're restoring GRUB.
Did you read this: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) ?

> GRUB is more than just a boot loader, it is also the worlds best boot manager, meaning it is best installed to the Master Boot Record of the first hard disk. That way GRUB will be the first thing that loads when the computer starts. It allows you to boot Linux directly or boot another boot loader which can then load its own operating system(s).You should type "**setup (hd0)**", to install GRUB to MBR (#7).

Just use these steps:
> **Command line**

 
[LIST=1]
[*]Boot your computer up with Ubuntu CD
[*]Open a terminal window or switch to a tty.
[*]Go [SuperUser]("https://help.ubuntu.com/community/SuperUser") (that is, type "sudo -s"). Enter root passwords as necessary.
[*]Type "grub"
[*]Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
[*]Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
[*]Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
[*]Quit grub by typing "quit".
[*]Reboot and remove the bootable CD.
[/LIST]


---

### Post by EPurpl3 on 2010-02-28
Wow, thank you, i didnt really understood what grub really is in its essence but now everything is clear. Thanks

---

