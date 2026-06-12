---
title: "I would like to re install windows"
date: 2009-11-21
forum: General Help
---

### Post by Ladgalen on 2009-11-21
Hi all

I would like to delete and install windows XP on my laptot, I do not did that since I got it 4 years ago and it is too long for windows. But I have several questions.

On the web several pages said that when you install windows, grub is unreachable. Then I will have to install it with a live CD. Ok but they said that if I do that

sudo grub

grub> find /boot/grub/stage1 ou grub> find /grub/stage1

I will find a list of the partition where grub is installed. But the file stage1 do not exist for me. I have grub version 1.97beta4. Then I am afraid to not find my ubuntu partions after the installation.

How will I have to install grub after the installation ?

Have you any advice for me about reinstalling windows ? Will this delete ubuntu ?

Thanks

---

### Post by Ladgalen on 2009-11-21
Maybe some precision :

I am under Karmic Koala and it seams that I am using grub2. It is strange that it is version 1.97beta4 but my files look like grub2 files ...

---

### Post by lmarmisa on 2009-11-21
I suppose that you have a dual boot system with Ubuntu and XP.

If so, you could consider re-install XP in a different way: XP would be a virtual machine (guest system) running inside the Ubuntu system (host system).

I recommend you to use [http://www.virtualbox.org](http://www.virtualbox.org) . It works great. 

You would have no problem with grub if you chose this option because Ubuntu would be  the only bootable system.

You could format the old XP partition (fat32 or NTFS) creating a new ext4 or ext3 file system. You could define the virtual disks for one or more virtual machines (XP, Linux, etc) in this new partition. 

Other advantage is that you can define dynamically expanded virtual disks in such a way that the full size of the disk is allocated only if the disk is full.

You have to install one driver in the XP guest system (program GuestAdditions) in order to integrate completelly the mouse and the screen.

Virtual machines are not complex and my experience with them is very positive. That it is the reason because I recommend them.

Best regards,

Luis

---

### Post by Ladgalen on 2009-11-21
I ever know this solution. But my computer is not powerfull enough to use this. One or two yers ago I did that with ubuntu as a guest and XP as the host.

I prefer to have a true version of windows XP because it is better for game and itunes which are the two only reason why I keep XP on my laptop. And in my reminds, with virtualisation it is difficult to use usb port into the guest and the guest is realy slow. But maybe not now.

Thanks

---

### Post by lmarmisa on 2009-11-21
Ok. I understand you.

Don't worry about the grub2 re-installation. This is really not difficult.

You have to start your computer using a Ubuntu 9.10 Live CD, open a terminal and type

[B]sudo bash
fdisk -l[/B]

Take note here where is the Linux partition (for example /dev/sda1)

[B]mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda #no number here
update-grub2[/B]

Restart the system.

If the XP system was not detected in the previous update-grub2 from the LiveCD, repeat the command now:

[B]sudo update-grub2

[/B]I suppose that this time Xp will be added to the grub list, even if Xp is located in a different disk unit.

So, don't worry and re-install normally your XP because the grub recovery is really easy.

Best regards,

Luis

---

### Post by Ladgalen on 2009-11-21
```

> sudo fdisk -l
[sudo] password for vallverdu: 

Disque /dev/sda: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0xeede9d79

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1               1         261     2096451   de  Dell Utility
/dev/sda2   *         262        2811    20482875    7  HPFS/NTFS
/dev/sda3            2812        4086    10241437+  83  Linux
/dev/sda4            4087        9729    45327397+   5  Etendue
/dev/sda5            4087        4239     1228941   82  Linux swap / Solaris
/dev/sda6            4240        9729    44098393+  83  Linux

```

Thus I will have to do :

```
mount **/dev/sda3** /mnt
mount --bind /dev /mnt/dev
chroot /mnt
grub-install /dev/sda
update-grub2
```

I suppose that sda3 is "/" and sda6 is "/home" ...

---

### Post by lmarmisa on 2009-11-21
If you have any doubt, type

[B]mount
[/B]
and you will see whre is mounted the root / and where the home directory.

Best regards,

Luis

---

### Post by lmarmisa on 2009-11-21
... and don't forget to gain super-user privileges in the code!!!

**sudo bash**

I use this command in order to start a new bash shell with root privileges.

---

### Post by Ladgalen on 2009-11-29
Hello

Thank you all for your answer. I re installed windows, all worked nice. I found another tricks for grub which appeared simpler to me. It is the following link (but in french sorry) :

[http://doc.ubuntu-fr.org//tutoriel/comment_sauvegarder_le_mbr?redirect=1](http://doc.ubuntu-fr.org//tutoriel/comment_sauvegarder_le_mbr?redirect=1)

It says to backup the mbr and to restore it after. I did that and it worked nice. When I reboot my system ubuntu was here and worked perfectly. But when I try to start windows, a black screen says to me in english (for french people when the computer speak english it means that very bad things will append) "no such device .... " with a long number.

I supposed that when I install windows the new NTFS partition does not have the same id. When I restore the mbr there is always the old id of the windows partition and thus grub don't find it because it does not exist.

I looked in the file /boot/grub/grub.cfg. There is that

```

menuentry "Microsoft Windows XP Professionnel (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 20085250085224d6
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

And the number 20085250085224d6 is the one that appears when I try to boot windows.

How can I fix it ?

Thanks

---

### Post by john newbuntu on 2009-11-29
It appears like the MBR backup that you had was the old one (before
you reinstalled windows).  So you are not able to find the newly installed
windows partition. Try running "sudo update-grub2" again.

---

### Post by mmix on 2009-11-29
If you have livecd(usb/cdrom fedora/ubuntu), boot with it.

on fedora livecd, there is menu to erase HDD. erase it.

I would recommend that fresh Winxp installation on your HDD.

---

### Post by Ladgalen on 2009-11-29
Thank you all. I found the solution.

I have to update the file /boot/grub/grub.cfg where there is the UUID of the windows partition. When I restore the mbr the UUID of the windows partitions was false because the fresh windows install create a new UUID. 

I did that and it work perfectly :

```
grub-mkconfig -o /boot/grub/grub.cfg
```

Thank again

---

