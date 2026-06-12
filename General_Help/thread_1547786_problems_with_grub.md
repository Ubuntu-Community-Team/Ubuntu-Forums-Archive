---
title: "problems with grub"
date: 2010-08-07
forum: General Help
---

### Post by arvindsubramaniam on 2010-08-07
I installed ubuntu on my sata disk from my laptop which has windows vista in it. After installing ubuntu, if i disconnect the SATA disk and reboot my laptop i get
 
"
no such hard drive detected
grub rescue >
"

But if the sata disk is connected, i get the grub page from which one chooses the operating system which they want to boot.

I am not able to access my windows vista without the sata disk being connected.

What do i do?

---

### Post by 23dornot23d on 2010-08-07
I have 2 USB drives ..... connected most of the time to my laptop and get a similar problem ....

when I disconnect them .... I get the same error as you get ........

___________________________________________________

My way around this is to use a separate USB stick with a boot loader on it .

___________________________________________________

Then its just a case of adding that when I want to take the laptop out ......

also a nice little security feature in a way ..... ( got to think positive )

because the laptop is a brick without the

USB stick boot loader.

---

### Post by oldfred on 2010-08-07
You installed grub to the internal drive. You should install grub the the external drive and reinstall a windows boot loader to the internal. Then in BIOS set the computer to boot the external first. If external not found it will boot windows in the internal.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Also to get grub to remember to install to the external.
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you use the external on many systems you should choose no drive to install to as it saves the location by drive (sda,sdb etc) not UUID. so if it is normally sdb but you also plug into another system where you already have a sdb it may still install to the wrong drive.

---

