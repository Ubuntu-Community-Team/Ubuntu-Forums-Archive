---
title: "preventing a broken os from booting"
date: 2011-12-22
forum: General Help
---

### Post by Fenderian_Mayhew on 2011-12-22
i need to prevent a previous os from loading. grub always list's it first and new kernels aren't being listed after upgrade. i think the grub from the other os is overriding the new one. how do i make the other partition have no boot info and make my current the default

i have used the startup manager (Grub setup gui) and the dead os's bootloader still remains, and loads. 

can post anything you can explain how to get. Thanks y'all

---

### Post by jjex22 on 2011-12-22
hi there, sorry to hear you're having problems, just to check, do I understand the problem is this:

You've removed a distro, installed a new one, but the original distro's grub is still in charge?

This usually means that either the installer didn't install grub, (as happened to me with fedora 16) or it installed the boot loader to it's / or /boot partition.

Would you mind supplying a little more information? For example which version of grub you are getting - 0.97, 1.97, 1.99, Grub4Dos, etc and which distros are involved? 

for example the command you probably want from inside linux is grub-install /dev/sda, but things get a bit distro specific after that, for example...

Debian based distros use grub2 (1.97-1.99) and update-grub i.e.
```

sudo grub-install /dev/sda
sudo update-grub

```

Fedora 16 also uses Grub 2, but not update-grub -
```

su -c 'grub2-install /dev/sda'
su -c 'grub2-mkconfig -o /boot/grub2/grub.cfg'

```

Arch and SUSE both use Grub legacy so you'd install grub with
```

su && grub-install /dev/sda

```
then edit the /boot/grub/menu.lst file if you had dual boot issues.

---

### Post by Fenderian_Mayhew on 2011-12-23
actually, i had 2 Ubuntu instalations (11.04, studio 10.04.4)  and  windows. my 11.04 died after i installed KDE-full beacuse kde and unity  wouldn't be friendly. now i use Ubuntu studio 10.04.4 but the 11.04  bootloader is still dominating so the broken 11.04 boots first.

Grub  1.97 is used by the 11.04 os but i want to use G2 for Studio 10.04.4. i  like the high res display and background image option.

the 11.04 is still installed on another partition

---

### Post by jjex22 on 2011-12-23
ah right I think what's happened here is that studio has installed grub to the mbr, then configured it, but as both are ubuntu, it's but 11.10 above the 10.04 based studio? (are both distro's available in the boot order?) because it's a later version

The reason I think this is that you say the 1.97 bootloader is in charge, but 11.04 uses 1.99 (both are grub 2)and 10.04 used 1.97

so long as both distro's are booting from the bootloader, it's not too much of a problem. If you wanted to get 1.99 back it should just be a case of booting into 11.04 and running sudo update-grub. 

either way if you want to change the boot order for the grub menu entries, boot into the distro that controls it (if grub 1.97, ubuntu 10.04, if grub 1.99, ubuntu 11.04) and follow this [ehow]("http://www.ehow.com/how_6921272_do-grub-boot-menu-order_.html")

hope it helps!

Edit [THIS]("http://www.psychocats.net/ubuntu/puregnomenatty") may help to fix the KDE problem by removing some of the problem packages, to add kde to unity it's best to use the kde plasma package, or smaller (minimal, base etc.)

---

### Post by Fenderian_Mayhew on 2011-12-26
The problem is 11.04 is broken and should never boot again. what do i have to delete for update-grub to ignore the 11.04 partition.

---

### Post by sirspazzolot on 2011-12-26
if you never ever want to use that broken partition again and have no interest in fixing it, then I would boot into the installation that you want to be in charge of GRUB, run gparted, and delete the broken partition. then reinstall grub to /dev/sda, and install [daniel richter's grub customizer]("https://launchpad.net/~danielrichter2007/+archive/grub-customizer") and have a jolly old time doing stuff like adding background images and renaming entries to something reasonably short. but that's just what I would do.

---

### Post by Fenderian_Mayhew on 2011-12-28
what i mean is, which files would one have to remove from the OS to rend it Un-findable by "grub-update" all the files i had on 11.04 are still good and usable, exactly where they are. I just want to make grub ignore it by deleting the files it looks for in the file system

---

### Post by utnubuuser on 2011-12-28
Boot Repair is another option for ya...
[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair]("http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair")

---

### Post by sirspazzolot on 2011-12-29
oh, I get what you want. someone else should confirm this but I think you could just delete /boot and grub won't find the partition, but you'd still be able to mount it.

---

