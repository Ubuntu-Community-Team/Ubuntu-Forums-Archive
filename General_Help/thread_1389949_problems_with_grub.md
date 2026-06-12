---
title: "problems with grub"
date: 2010-01-25
forum: General Help
---

### Post by samjog on 2010-01-25
Hi
I had My C drive partitioned into 30 gb for ubuntu 9.01 and 110 gb for windows vista.
I have replace vista with windows 7 but now the grub does not load ,and i have no access to linux..can someone please help me

---

### Post by lindsay7 on 2010-01-25
If you have not installed grub2. This should fix it.


Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window 
3. Type &#8220;sudo grub&#8221;. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Note:  Do not type in the quotation marks in the commands.


If you have grub2 installed do this.  You say you have Ubuntu 9.01 so I am not sure what version you have!

Howto Recover Grub2 After Windows Installation 
Posted by Binbash on Jun 21, 2009 
Labels: grub2, Howto, jackalope, jaunty, karmic, koala, linux, recover, ubuntu, windows 
Today i destroyed my Grub2 via installing windows on my notebook which i write blog posts.(I quit smoking , so i have to play some games : ) No rush). It may be hard to recover it since there are not much (i did not find anything) howtos around the net about recovering Grub2.Here is the step by step guide to recover it :

You will need a LIVE cd if you are going to recover an Ubuntu Box.Download Ubuntu Jaunty, Karmic whatever you want.Open the system with Live CD (I assume you are using Ubuntu Live CD).Press Alt+F2 and enter gnome-terminal command.And continue by entering :

$sudo fdisk -l

This will show your partition table.Here is my table to understand it better :

/dev/sda1 29 8369 66999082+ 83 Linux
/dev/sda2 * 8370 13995 45190845 7 HPFS/NTFS
/dev/sda3 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Now i will mount Linux (sda1 here), i have no external boot partition as you can see.(IF YOU HAVE external one, do not forget to mount it! )

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc

The following command is optional (it copies resolv.conf)

$sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

Now chroot into the enviroment we made :

sudo chroot /mnt

After chrooting, you do not need to add sudo before your commands because from now, you will run commands as root.

You may want to edit /etc/default/grub file to fit your system (timeout options etc)

#nano -w /etc/default/grub

Play with the options if you want.(But do not forget to give grub-update command if you saved it ;) )

Now install/recover Grub2 via :

#grub-install /dev/sda

command.However you may get errors with that code like me.If so please use this command :

#grub-install --recheck /dev/sda

Now you can exit the chroot, umount the system and reboot your box :

#exit
$sudo umount /mnt/dev
$sudo umount /mnt/proc
$sudo umount /mnt
$sudo reboot

---

