---
title: "How to uninstall Ubuntu 11.04"
date: 2011-05-05
forum: General Help
---

### Post by Black Rain on 2011-05-05
I have win7 and ubuntu 11.04 separately . Its called dual boot i guess.

How do i uninstall ubuntu 11.04 but i messed up, only terminal is working as i uninstalled fluxbox and nothing seems to work.

But i think it should be uninstalled from the main os(in my case win7) as i installed from it.
So how can i do it.

I little detail shall be appreciated as i am not so much of a computer man.

---

### Post by Joe of loath on 2011-05-05
If you installed using Wubi (inside Windows), Ubuntu will be installed as a regular Windows program, and can be removed like any other program.

If you booted from the CD, just delete the partition you installed Ubuntu to, and either stretch your Windows 7 partition to fill the space, or reinstall Ubuntu into the deleted space.

---

### Post by Lateralis on 2011-05-05
As an addendum to the previous post, if Ubuntu is installed on a separate partition and not installed through Wubi, then the Grub boot loader will still persist in the MBR but will not be able to locate the grub files needed to boot the system.  So, if you no longer want to use Ubuntu you will need to reinstall the Windows boot loader, and I would personally recommend doing that *before* you delete the Ubuntu partition.  Once the Windows bootloader has been loaded into the MBR you can simply delete the Ubuntu partition using the tools built into Windows.  

If instead you wish to continue using Ubuntu or any other flavour of Linux, you can simply use the install CD/LiveCD for the distro to overwrite your Ubuntu installation and there will be no need to reinstall the Windows bootloader.

---

### Post by Black Rain on 2011-05-05
> **Lateralis said:**
> As an addendum to the previous post, if Ubuntu is installed on a separate partition and not installed through Wubi, then the Grub boot loader will still persist in the MBR but will not be able to locate the grub files needed to boot the system.  So, if you no longer want to use Ubuntu you will need to reinstall the Windows boot loader, and I would personally recommend doing that *before* you delete the Ubuntu partition.  Once the Windows bootloader has been loaded into the MBR you can simply delete the Ubuntu partition using the tools built into Windows.  

If instead you wish to continue using Ubuntu or any other flavour of Linux, you can simply use the install CD/LiveCD for the distro to overwrite your Ubuntu installation and there will be no need to reinstall the Windows bootloader.


Thanks for the help Lateralis, but i have completely no idea what you are talking about. I have read it a couple of times but understood nothing.

All i get is before i delete ubuntu partition i got to reinstall windows boot loader?
But what is Windows boot loader and how to reinstall it?

I have installed it from universal usb installer and not wubi.

So sorry to ask stupid question but i am not intelligent and geek. :(

---

### Post by mdhollis on 2011-05-05
If you have the windows 7 disk, follow this link.

[http://www.windowsreference.com/windows-7/how-to-reinstall-windows-7-boot-loader/]("http://www.windowsreference.com/windows-7/how-to-reinstall-windows-7-boot-loader/")

Then boot into windows.  Go to the control panel-> administrative tools-> computer management-> disk management then format the linux partition to ntfs.  That will remove ubuntu completely.

---

### Post by openation on 2011-09-26
i cant get my gateway to work my wireless broadcom with ubuntu. I dont know how to do it myself. i like ubuntu a lot.

---

