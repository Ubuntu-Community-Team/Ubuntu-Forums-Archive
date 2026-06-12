---
title: "Fixing the MBR after Windows installation.(GRUB2)"
date: 2011-08-17
forum: General Help
---

### Post by Mister LinOx on 2011-08-17
Okay, so about three months ago I, without thinking, reinstalled my windows installation after already having the dual-boot set up and it wrote over the GRUB with Windows MBR. I let my girlfriend's friend borrow the disc before this and decided to just wait it out. Then, when getting the disc back, I carelessly forgot it at their house and have never been able to retrieve it, nor do I think that I ever will. 

SO. At this point my only live discs either only have GRUB1 or are corrupted. My only tools now are a netbook with a wubi installation of Xubuntu(no CD drive) and a 1GB flash drive, it seems. Any suggestions on how to access my ubuntu installation?

---

### Post by n213978745 on 2011-08-17
Use your Windows and go to the following website:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

Download Easy BCD 2.1, it's free IF it's for home use, for business use, I think they will ask you to pay.

After installing it, 
go to tab "Add New Entry,"
Click Linux/BSD
Choose under the "device" menu and select which partition you install your Linux then click ok.

Saving your setting and try to reboot and see if you can access your Linux via this Windows bootloader.
P.S. I might miss some steps

Once you access to Linux, go to the following website:
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

See if you can fix it via this method or not, finally let us know about it ;)

---

### Post by Mark Phelps on 2011-08-17
Even though I'm a big fan of EasyBCD (on Windows PCs), I'm wary of doing what was suggested here.

Why?

Because when I looked into this a while back, EasyBCD did not use GRUB but used, instead, a Windows variant of GRUB know as GRUB4DOS.  It HAD to do that because it installed the boot loader into an NTFS partition -- which, as far as I know, you can't do with the real GRUB.

So, if that's the case, and you can boot with EasyBCD, and you then UPDATE it using GRUB2, one of two things is likely to happen:
1) You break the EasyBCD implementation of GRUB and can't boot into Ubuntu anymore
2) You break the Windows boot (by forcing GRUB into the Windows boot partition) and can't boot Windows anymore.

---

### Post by Mister LinOx on 2011-08-17
I'm trying Rescatux currently. It's setting up on my USB drive. It looked promising and hopefully it works out well. ^.^ Thank you for the extra suggestion, though.

---

### Post by n213978745 on 2011-08-17
> **Mark Phelps said:**
> Even though I'm a big fan of EasyBCD (on Windows PCs), I'm wary of doing what was suggested here.

Why?

Because when I looked into this a while back, EasyBCD did not use GRUB but used, instead, a Windows variant of GRUB know as GRUB4DOS.  It HAD to do that because it installed the boot loader into an NTFS partition -- which, as far as I know, you can't do with the real GRUB.

So, if that's the case, and you can boot with EasyBCD, and you then UPDATE it using GRUB2, one of two things is likely to happen:
1) You break the EasyBCD implementation of GRUB and can't boot into Ubuntu anymore
2) You break the Windows boot (by forcing GRUB into the Windows boot partition) and can't boot Windows anymore.

m... I am not sure I follow you.  Before the EasyBCD 2.1 version, I did have problem with EasyBCD because it can't boot any Linux under the extended partition.

As far as... if you mean whether EasyBCD will break Ubuntu bootloader...  well I don't think you will break it because I am using it on my computer and is fine:
I first install Windows 7 then Ubuntu Linux, so when I boot my computer it will load the Grub2 bootloader and I can select whichever OS I want to boot.  Then I went over to Windows 7, install my EasyBCD latest version and edit the boot menu -- putting Ubuntu Linux into Windows bootloader.  I didn't write the bootloader into MBR, but only change the menu within Windows bootloader.

Now whenever I boot up my computer, it will go to Grub2 bootloader, I can then select either Windows 7 or Ubuntu.  Assuming I select Windows 7, the Windows 7 will display a boot menu, allow me to choose to boot either Windows 7 or Ubuntu Linux.  If I boot Windows 7, it boot to Windows 7 login screen.  But if I select Ubuntu Linux from the menu, it will boot back to Grub2 bootloader and let me select whether I want to boot Windows or Linux again.


I am NOT sure is that what you are asking for, but as far as my Windows and Linux go, both bootloaders are fine.

---

### Post by Mister LinOx on 2011-08-17
I ended up using EasyBCD, but rather than fixing the GRUB afterward, I'm just going to keep it how it is to not risk what Mark stated. It's simply set up as:

>Ubuntu
Windows Vista

And the Ubuntu field just loads up the GRUB as usual. ^.^ Thank you for the help.

---

