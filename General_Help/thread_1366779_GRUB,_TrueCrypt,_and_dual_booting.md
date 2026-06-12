---
title: "GRUB, TrueCrypt, and dual booting"
date: 2009-12-28
forum: General Help
---

### Post by Trentor on 2009-12-28
I am trying to install True Crypt for my Windows 7 partition on my laptop, but it requires that it be installed in the MBR, therefore I cannot have my GRUB installation in the MBR, I must move it to its own partition they suggest.

I was having some issues with my old 9.04, so I deleted the partition and ran Windows 7 fixmbr, so the windows bootloader is now in my MBR.

I just did a fresh install of Ubuntu 9.10, made a new ext2 partition in /dev/sda1 thats 7mb, enough for GRUB, and at the end of the installer I selected the boot loader to be installed in /dev/sda1

My partition I want GRUB in is 7mb /dev/sda1
My partition for swap is 1GB /dev/sda2
My partition for ubuntu is 12GB /dev/sda4
My partition for windows 7 is 128GB /dev/sda3

So after the reinstall, the MBR is still the windows MBR and the grub menu does not show up, why is this even though I specifically said for grub to be installed on its own partition.

Thanks in advance!

Edit: I am using gparted to edit my partitions, I tried adding the boot flag to /dev/sda1 and now the GRUB menu shows, but what I am wondering if this means it is now in MBR?

Trentor

---

### Post by Trentor on 2009-12-29
Bump, and anyone got any insight?

Trentor

---

### Post by Trentor on 2009-12-29
Bump, anyone? :confused:

---

### Post by Trentor on 2009-12-30
Bump, still no-one? :(

---

### Post by spigy11 on 2009-12-30
Hi

I need to restore my grub either so Im suggesting to use some of the following nice links to do this

[http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala](http://linuxers.org/howto/how-recover-grub2-ubuntu-910-karmic-koala)

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)


Hope that helps

---

### Post by meierfra. on 2009-12-30
> I tried adding the boot flag to /dev/sda1 and now the GRUB menu shows, but what I am wondering if this means it is now in MBR?
No. It means that Grub is in the boot sector of  /dev/sda1.  A windows MBR just  loads the code in the boot sector of the partition with the boot flag.

---

### Post by Trentor on 2010-01-04
So if the previous is true, then I am assuming that the TrueCrypt MBR will guide itself to the grub partition if I choose not to boot into Windows 7 with AES encryption..  hmm thanks for the information

---

