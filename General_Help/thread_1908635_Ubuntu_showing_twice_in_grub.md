---
title: "Ubuntu showing twice in grub?"
date: 2012-01-13
forum: General Help
---

### Post by alexp11 on 2012-01-13
Hello, I am tri-booting with windows 7, Linux mint 11, and Ubuntu 11.10. When my grub loads, it has ubuntu showing up 4 times. I understand it should show up twice, once regular and once for recovery, but I have two of each, but both go to the same partition /dev/sda6. The only difference is the numbers at the end. one is 3.0.0-2 and the other 3.0.0-4. Do I need both of these? I had burg installed, but it was cluttered with 4 Ubuntus as well as the 2 mints and 2 windows. So, if I don't need them both, how would I remove one, and which should I remove? From what I have searched it seems the numbers are the kernels? I'm new to the Linux operating systems, but so far I love mint and am getting used to Ubuntu. :) Thanks for help in advance.

---

### Post by Dennis N on 2012-01-13
you will have a grub entry for each kernel found on each partition, and a recovery mode entry for each. The old ones are not automatically deleted when a new one is installed by an update, in case the new one causes some problem and you then can revert to using the older one.

---

### Post by alexp11 on 2012-01-13
Ah, is there anyway to possibly hide the older one? It just seems really clustered on the boot, I like things to look as clean as possible. But if I boot either one, they will have the same files and installed programs, right?

---

### Post by drs305 on 2012-01-13
Normally with the latest Grub (1.99, you can check with "grub-install -v" ) you will have one kernel and one recovery option, with older kernels hidden in a submenu.

There are several ways of dealing with additional kernels, including hiding them (Grub Customizer) or removing them from your system (Ubuntu Tweak).

Here is a post about some of the available options. Most experienced users recommend keeping at least one older kernel which you know works in case the current kernel gets corrupted. Links to both are in my signature line, but here is the main link:

[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by bsniadajewski on 2012-01-13
You can remove the older one if you don't need it.  just do a sudo apt-get remove or purge on the linux-image-3.0.0-2-generic linux-headers-3.0.0-2 linux-headers-3.0.0-2-generic packages and Ubuntu will then update GRUB to reflect that.

---

### Post by Dennis N on 2012-01-13
You can remove the extra kernels. A safe way is to use the utility called Ubuntu Tweak. Here is one article that explains how to get it from a PPA:

[Ubuntu Tweak]("http://www.ubuntugeek.com/ubuntu-tweak-0-6-0-released-and-ubuntu-ppa-installation-instructions-included.html")

---

### Post by alexp11 on 2012-01-13
Well, I reinstalled burg, and that thread talks about grub, so if I do that and update grub to not have the extra kernels, would running the update burg command remove it from burg as well?

---

### Post by Dennis N on 2012-01-13
> **alexp11 said:**
> Well, I reinstalled burg, and that thread talks about grub, so if I do that and update grub to not have the extra kernels, would running the update burg command remove it from burg as well?

Which bootloader is not important if you use the Ubuntu Tweak (see post 6). It will find the extra kernels, and give you the option to remove them.

---

### Post by alexp11 on 2012-01-13
Alright, I'm working on it now. Tried to install tweak while I was running mint. lol Now I'm working on it right now and will post if I need anymore help, thanks everyone. :) I love how helpful the communities for these OS's are. :D Edit: its showing 3 unused kernels, is it possible it will list my Linux Mint kernels, or is it all Ubuntu?

---

### Post by Dennis N on 2012-01-13
> **alexp11 said:**
> Alright, I'm working on it now. Tried to install tweak while I was running mint. lol Now I'm working on it right now and will post if I need anymore help, thanks everyone. :) I love how helpful the communities for these OS's are. :D Edit: its showing 3 unused kernels, is it possible it will list my Linux Mint kernels, or is it all Ubuntu?

No. When you run it from Ubuntu, you only can remove the old Ubuntu kernels.

---

### Post by alexp11 on 2012-01-13
> **Dennis N said:**
> No. When you run it from Ubuntu, you only can remove the old Ubuntu kernels.

I was just coming back to update to say after looking at the file names I saw it was 3 parts of 1 kernel and I removed it and the extra Ubuntu options are gone, now to try go hide the recovery loaders... Edit: Got it using the grub customizer linked to in the guide posted. Thanks everyone. :)

---

### Post by xyzzyman on 2012-01-14
Unless you'll remember what commands to type manually, you may want to keep the recovery options in your grub menu... Otherwise you may find yourself having a flat wondering why you took the jack out of the trunk. :)

---

