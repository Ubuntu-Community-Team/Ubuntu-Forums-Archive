---
title: "Uninstalling?"
date: 2010-07-27
forum: General Help
---

### Post by Travisasdf on 2010-07-27
I need help uninstalling Ubuntu. I like it and its good but I dont really have any use for it and I can't use anything I own with it.

Currently I have it installed on a 15gb partition on my hard drive. And I have no clue how to uninstall it I just want to get it off of the hard drive so I can boot into windows without having to choose everytime. So if uninstalling is really complicated is their a way to make it so Windows boots by default?

Note- I tryed doing that gksudo gedit /boot/grub/menu.lst command thing to make windows the default but all i get is a blank text file.

---

### Post by howefield on 2010-07-27
> **Travisasdf said:**
> Note- I tryed doing that gksudo gedit /boot/grub/menu.lst command thing to make windows the default but all i get is a blank text file.

startupmanager is an application which makes it easy set your operating system default. It can be installed with Synaptic Package Manager.

Otherwise you will need to restore your MBR using a windows disk and then simply delete the Ubuntu partition.

PS. There is no menu.lst in later version of Ubuntu, I think Karmic onwards which uses Grub2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Darkness Des on 2010-07-27
Sorry to see you go. The reason your editing of that file is because 10.04 uses a different bootloader than the version the outdated guide uses. You can use just about any partitioning tool to remove your Ubuntu partition, but that (probably) won't remove the bootloader. Someone else will have to answer on making Windows boot by default, I'm not very good with editing the boot entries.

---

### Post by Travisasdf on 2010-07-27
EDIT: Lol nvm i found it. Derr

---

