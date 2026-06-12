---
title: "Uninstalled Ubuntu and Can't boot"
date: 2011-12-13
forum: General Help
---

### Post by SSTUTO on 2011-12-13
I have an HP computer with 80 gb solid state drive with Windows 7 64 bit home edition installed. I had UBUNTU installed as well. It started created start up issues on its on. The boot order got changed and it defaulted to ubuntu. 

I followed these instructions to uninstall ubuntu
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

Now I am getting the error that GRUB is missing. I am not a computer programmer so I don't speak this language. I did have a restore disc I created the day I brought the computer home. A friend helped me image the hard drive and create a restore disc. 

When I went to use it today, it does not work. I click to boot from cd on start up and get this error:


"Windows has encountered a problem communicating with a device connected
to your computer. 

This error can be caused by unplugging a removable storage device such as an external USB drive while the device is in use, or by faulty hardware such as a hard drive or CD-ROM drive that is failing.

Make sure any removable storage is properly connected and then restart your computer.


File: \windows\system32\boot\winload.exe

Status: 0xc00000e9

Info: An unexpected i/o error has occurred"


I do not know what else to do. I want to restore my computer to Windows 7 only and maintain all operating system and programs on my 80gb solid state drive as always. I just don't want to deal with ubuntu anymore. Can anybody help me out further? Is my Restore Disc bad? If so what do I do?

---

### Post by zvacet on 2011-12-14
Probably there is easier solution,but I´m not awere of it so you can do this:

1. install ubuntu again (if you still have Windows) on same partition as you did last time.That should allow you to boot in Windows.Then do 

2.[http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe](http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe)
3.after thar you can delete ubuntu partition and boot in Windows

---

### Post by Mark Phelps on 2011-12-14
If you're lucky, only the MBR or boot loader need repairing, and Boot-Repair can do that for you:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

If, however, you've trashed Win7 in thrashing around with Ubuntu removal, you would likely have to reinstall it, and given you don't have an installation DVD, that means running the factory restore -- and losing all your data, settings, and apps.

---

