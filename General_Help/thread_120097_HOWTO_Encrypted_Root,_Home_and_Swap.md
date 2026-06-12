---
title: "HOWTO: Encrypted Root, Home and Swap"
date: 2006-01-20
forum: General Help
---

### Post by heitor_capovilla on 2006-01-20
**[SIZE=4][FONT=Arial, Helvetica]Ubuntu 5.10 (Breezy Badger) with encrypted Root, Home and Swap[/FONT][/SIZE]**[SIZE=2][I]
by Rud&#225; Moura (ruda.moura@gmail.com)[/I]

This is the way I did to get an Ubuntu 5.10 (Breezy) with full encrypted file system: root (/), home and swap. Since Ubuntu installer does not support yet this option, this process concerns, first, installing Ubuntu on a temporary partition and then, inside that instalation, preparing all the encrypted partitions for the OS. The old root which I used in the beginning is turnt into a swap partition.

This fully encrypted filesystem method employs dm-crypt, linux kernel's devmapper and cryptography. The default algorithm is AES (aes-cbc-plain) with 256bits key. Mark that I am not a *connoceur* on the subject or even a *crypto freak*, I just can say that this worked for me.

[B]
Part 1: Ubuntu installation[/B]

Install Ubuntu with *server profile* with the following initial partitioning scheme:

[FONT=Courier New]/dev/hda1 /boot 100 MB ext3
/dev/hda2 / 512 MB ext3 [/FONT]

Mark that 512 MB is really the shortest size you can set for a server type of installation. A complete Ubuntu installation requires at least 2.4 GB. Make your choice now. In addition, I created two more spaces to hold my future encrypted root and /home partitions, so as the following:

[FONT=Courier New]/dev/hda3 future / 10GB
/dev/hda4 future /home 30GB [/FONT]

Set these partitions in the installer option for filesystem as "do not use the partition". Note that it is not absolutely necessary to have an exclusive /home partition, so this is optional since you can have only one partition for a whole encrypted system. Just ignores the alert about not having a swap partition and keep walking.

[B]
Part 2: Cryptography software installation[/B]

Configures your apt to use all the optional repositories which come with Ubuntu. This is done by modifying /etc/apt/sources.list, uncommenting all the &#8220;deb&#8221; repositories. Since you are on a terminal with no gedit or something like that, you will need a pure text editor such as Vi. If you know how to use it, don't care for the following explanation for begginers: to edit text files on a terminal using the Vi command, follow this example:

[FONT=Courier New]# vi /etc/apt/sources.list[/FONT] 

Press &#8220;i&#8221; to enter in the INSERT mode, make the alterations, press ESC to enter the COMMAND mode and then press SHIFT+zz (ZZ) to save and quit.

Just install the following additional packages: crypsetup 1.0.1, hashalot 0.3, initrd-tools 1.78 e cramfsprogs 1.1 with the command:

[FONT=Courier New]# apt-get install cryptsetup hashalot initrd-tools cramfsprogs[/FONT]

Important: **initrd-tools must be updated to 1.78 version**, because the original one that comes with Ubuntu has a severe bug which makes it unusable.


**Part 3: Creating the encrypted system**

Now it is time to create the cryptography devices. First, root: choose a trustworthy password, so that you will not end with a weak security implementation. Do not even use your personal login password. Observe that it is hard to change this password later (you would need to re-encrypt the full system again) and this is not explained in this article. The password for /home can be more weak, because it will be stored encrypted inside the file /etc/keys/home (remember that / is being fully encrypted). This is necessary to avoid that /home password would be asked at every boot in order to be mounted.

[FONT=Courier New]# cryptsetup -y create root /dev/hda3
# sha256 > /etc/keys/home
# cryptsetup -d /etc/keys/home create home /dev/hda4 [/FONT]

The password for root will be asked twice, but the one for /home will be asked only one time and it does not provide confirmation! The partitions with support for cryptography will be available at /dev/mapper/. Now create the filesystem. I prefer the XFS filesystem and, before we continue, let me make a point on it: this is the one for high performance boxes created by Silicom Graphics, with no undelete policies and 64bit technology. Also there are not tools for Windows which can be used to mount a XFS filesystem. Anyway, who cares since now we are going to be encrypted! You can use any filesystem supported by Ubuntu and the one everyone use is ext3, but that's a matter of taste.

[FONT=Courier New]# mkfs -t xfs /dev/mapper/root
# mkfs -t xfs /dev/mapper/home [/FONT]

If you want to use an Ext3 filesystem, just change both xfs references above to ext3 so that it will be as the following:

# mkfs -t ext3 /dev/mapper/root
# mkfs -t ext3 /dev/mapper/home 

Now mount the new partitions to /mnt and copy the old root to the new one at /mnt. This will be a perfect copy, preserving data, symbolic links and everything.

[FONT=Courier New]# mount /dev/mapper/root /mnt
# mkdir /mnt/home
# mount /dev/mapper/home /mnt/home
# cp -axv / /mnt 
[/FONT]
The copy process took two minutes and a half for a server profile and sixteen minutes for a complete installation. Mount /dev inside /mnt/dev to get access to the devices.

[FONT=Courier New]# mount --bind /dev /mnt/dev [/FONT]


**Part 4: Adjusts inside chroot**

Enter the encrypted system by using the chroot command and mount /boot, /proc and /sys:

[FONT=Courier New]# chroot /mnt
# mount /boot
# mount /proc
# mount /sys [/FONT]

This step **must be done **in order to fix a bug in Ubuntu, but do not ask me why..

[FONT=Courier New]# ln -sf /lib/libdevmapper.so.1.01 /lib/libdevmapper.so.1.00 [/FONT]

Edit /etc/crypttab and add the following lines:

[FONT=Courier New]root /dev/hda3
home /dev/hda4 /etc/keys/home 
[/FONT]
Edit /etc/fstab in order to change root to the new mounting point at /dev/mapper/root **and add a line for /home**. I did it this way:

[FONT=Courier New]/dev/mapper/root / xfs defaults 0 1
/dev/mapper/home /home xfs defaults 0 2 [/FONT]

Edit /etc/kernel-img.conf and add the following line:

[FONT=Courier New]ramdisk = /usr/sbin/mkinitrd [/FONT]

Edit /boot/grub/menu.lst, search for kopt and change this line to:

[FONT=Courier New]# kopt=root=/dev/mapper/root devfs=mount ro [/FONT]

Note that the initial # should NOT be removed!

Asks it to reconfigure kernel so that it obtains a new file for grub and a new initrd image able to support cryptography.

[FONT=Courier New]# dpkg-reconfigure linux-image-2.6.12-9-386 [/FONT]

This command takes into consideration that the installed kernel is the original one from the installation, but if it is NOT the case, substitute it properly &#8211; for example, 686 instead of 386, or any other updated version.

[B]
Part 5: Finishing[/B]

Unmount all chroot file systems, quit chroot and reboot:

[FONT=Courier New]# umount -a
# exit
# reboot 
[/FONT]
If everything worked fine, your system will ask for the password in order to mount /root and then the boot process will continue. If you type a wrong password the system will not output any alert and will fail drastically, probably with a Kernel Panic.

[B]
Part 6: Encrypted Swap 

[/B]This process is like the other we done for /home, but the only difference is that the password will be different for every *boot*, since it will be read from /dev/random.
[FONT=Courier New]
# cryptsetup create swap /dev/hda2 [/FONT]

Type any garbage as password, since it will not be typed by the user. 

Edit /etc/crypttab and add the line for swap:

[FONT=Courier New]swap /dev/hda2 /dev/random swap [/FONT]

Edit /etc/fstab and add the file for swap:

[FONT=Courier New]/dev/mapper/swap none swap sw 0 0 [/FONT]

To enable swap immediately:

[FONT=Courier New]# cryptsetup remove swap
# /etc/init.d/cryptdisks start
# swapon -a [/FONT]

From this moment your whole filesystem is encrypted. In order to turn your server instalation into a default and complete one, just do it:
[FONT=Courier New]
# apt-get install ubuntu-desktop [/FONT]

The following sources were checked for writing this article: crypsetup(8), crypttab(5), [/SIZE][_[SIZE=3][COLOR=#000080]http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO[/COLOR][/SIZE]_]("http://www.saout.de/tikiwiki/tiki-index.php?page=HOWTO")[SIZE=2]

[/SIZE]   	 	 	 	 	 	 	 	  [SIZE=2][FONT=Times New Roman, serif]Original article: [http://www.livejournal.com/users/rstm/1999.html]("http://www.livejournal.com/users/rstm/1999.html") [/FONT][/SIZE] 
 [SIZE=2]Translation from Brazilian Portuguese to English: Heitor Capovilla ([/SIZE][EMAIL="heitorcapovilla@hotmail.com"]_[SIZE=2][COLOR=#000080]heitorcapovilla@hotmail.com[/COLOR][/SIZE]_[/EMAIL][SIZE=2])[/SIZE]

---

### Post by cabavil on 2006-02-06
Hello,

you did a good job on this tutorial !!! 

But I have a question: Did you heard of use the "LUKS" options for the cryptodevices ?
[http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS](http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS)
It would make the multiuser enviroment a little easier. 

Did you try it and i didn't worked ? Or did you never heard of it ?

Sincerly

Norbert

---

### Post by kubuntu2k6 on 2006-02-10
Very nice tutorial!

Will try this soon...

---

### Post by dcstar on 2006-02-10
Please repost in the "Customization Tips and Tricks" forum.

---

### Post by honeydew on 2006-04-12
when I do dpkg-reconfigure linux-image-2.6.12-9-386

I get the error

faild to create initrd image.

I tryed installing the initrd-tools (debian .84)pakage but had no luck..

---

### Post by honeydew on 2006-04-12
retried and worked.. prolly a typo somewhere... thanks for the howto =]

---

