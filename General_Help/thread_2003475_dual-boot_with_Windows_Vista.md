---
title: "dual-boot with Windows Vista"
date: 2012-06-14
forum: General Help
---

### Post by virsto on 2012-06-14
I have earlier partitioned my HD for dual-boot of Windows Vista and Ubuntu on a 32-bit PC platform. When I booted up my system I always was presented with a list of different versions of Ubuntu and Windows Vista which allowed to choose my OS. Recently, for no obvious reason, I never see this list in which I can choose the OS. Instead it always boots into Windows Vista. I am quite sure that the Ubuntu OS is there; but, I never get a chance to boot into it.

Why does this occur and how can it be fixed so that I am able to choose my OS?

---

### Post by naknak987 on 2012-06-14
I'm not sure why this happend to you, it shouldn't have happend. To fix this though you can use any boot loader thats compatible with windows 7 and ubuntu 10.04 if thats what your still using. Heres a link to a tutorial for setting up the grub bootloader with multiple operating systems. [http://www.dedoimedo.com/computers/grub.html]("http://www.dedoimedo.com/computers/grub.html")
I also found this in the ubuntu documentation, it may help. [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by sgage on 2012-06-14
> **virsto said:**
> I have earlier partitioned my HD for dual-boot of Windows Vista and Ubuntu on a 32-bit PC platform. When I booted up my system I always was presented with a list of different versions of Ubuntu and Windows Vista which allowed to choose my OS. Recently, for no obvious reason, I never see this list in which I can choose the OS. Instead it always boots into Windows Vista. I am quite sure that the Ubuntu OS is there; but, I never get a chance to boot into it.

Why does this occur and how can it be fixed so that I am able to choose my OS?

You can boot the installation media for Ubuntu and chroot to your installation, then run:

sudo grub-install /dev/sda
sudo update-grub

Then you should boot back to the grub menu as before.

Another alternative is to chroot as above, but install grub on the Ubuntu partition itself instead of the MBR:

sudo grub-install -f /dev/sdax (where x is the partition number of your Ubuntu)
sudo update-grub

You will reboot to Windows as you have been. In Windows, download the free and excellent EasyBCD and make an entry for Linux. Tell it grub-2, not legacy grub. Set the menu delay for whatever you like. 

When you reboot, you'll be offered a chance to boot into Linux. This is how I typically do things on a dual-boot rig - Windows will not hibernate if it does not "own" the MBR.

---

### Post by GreatDanton on 2012-06-14
If you have live cd of Ubuntu then take a look at this site:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It's very easy to repair grub menu with this software.

---

### Post by Mark Phelps on 2012-06-14
Some PC, most notably Dells (but maybe others as well), have software built in that periodically checks the content of the MBR against a saved copy, and if it is found to be different, overwrites the MBR from the saved copy.

This would effectively remove any GRUB code from the MBR and return you to your pre-dual-boot state.

If that is the case with your PC, rewriting the MBR is only going to lead to this same problem again and again.

The EasyBCD solution recommended does not mess with the MBR, and while it's more work, it won't get overwritten.

---

### Post by virsto on 2012-06-16
> **GreatDanton said:**
> If you have live cd of Ubuntu then take a look at this site:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It's very easy to repair grub menu with this software.

This worked perfectly --- thanks for the tip/link GreatDanto-

---

### Post by GreatDanton on 2012-06-17
You're welcome. I am glad it works for you.

---

