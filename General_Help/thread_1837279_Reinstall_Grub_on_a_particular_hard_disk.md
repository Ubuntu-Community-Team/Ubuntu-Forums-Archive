---
title: "Reinstall Grub on a particular hard disk"
date: 2011-09-01
forum: General Help
---

### Post by FormatSeize on 2011-09-01
Hello, all. 
I have three hards disks, sda, sdb, and sdc. They each have a different Linux disto, with Ubuntu 11.04 being on sda. Right now, that's what I have been using most frequently for common everyday computer usage. sdc will only boot from USB, which is what I intended, and it seems to be unaffected by what happened. Yesterday, I decided that I would install Fedora 15 on sdb. So I install it assuming that whatever I did would only affect things on disk sdb.
 
Boy, was I wrong. I'm not completely sure how this happened, but the installation blew away the grub bootloader on disk sda. When I try to boot from sda, all I get is a blinking cursor and nothing else. No grub rescue prompt or anything - just a blinking cursor. 
 
There's got to be a way to get back into sda, I thought. So I install Xubuntu over Fedora on sdb. Okay. So, with grub installed on sdb, I'm able to select sda to boot, and I can get back to Ubuntu 11.04. The thing is, I don't always want to have to use this workaround. The only reason why Xubuntu is there is so that I can use it's grub to boot into Ubuntu; I don't use it at all. 
 
So the question is, how do I install grub on sda so that I can just cut on the computer and boot from the first hard disk? I don't like using an entire hard disk just so that I can use the grub menu. 
 
Thanks

---

### Post by Bucky Ball on 2011-09-01
You might try boot repair:

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

---

### Post by Blasphemist on 2011-09-01
Fedora does through some trickiness at you so do be careful when you install it. The easiest way to fix this is to install boot-repair from natty and use it to reinstall grub2 to sda. [http://ubuntuforums.org/showthread.php?p=10871917#post10871917](http://ubuntuforums.org/showthread.php?p=10871917#post10871917)

Go into the advanced options, choose to reinstall grub and have it install to sda.

---

### Post by YesWeCan on 2011-09-01
So the way things normally work, Grub2 needs both an MBR and a boot partition inside a linux OS.

If you set up Xubuntu in a partition on sda and use it to install Grub2 to the MBR of sda you are there. You just need a small partition for Xubuntu, say 5GB, unless you are going to use it for some other purpose than booting. You do not need to install any other Grubs anywhere.

Then, you can install new OSs all over the place as you like, including on sda, PROVIDED YOU DO NOT install Grub again, at least not to sda. Unfortunately, I think the Ubuntu installer does not allow you not to install Grub somewhere (d'oh) so you're best to install it to the OS partition itself (which will never be used).

Each time you install a new OS you would need to reboot into Xubuntu and run [COLOR="Navy"]sudo update-grub[/COLOR] to add it to the Grub menu.

This isn't the only way to do what you need but it is relatively easy.


Now, fedora 15 is a little interesting (it uses grub legacy by the way) and I advice not installing Grub at all (Anaconda lets you not install grub). Then reboot Xubuntu and install LVM which will facilitate Grub detecting fedora:
[COLOR="navy"]sudo apt-get install lvm2
sudo vgchange -ay
sudo update-grub[/COLOR]
and you will see fedora being added to the menu.

---

### Post by Blasphemist on 2011-09-01
> **YesWeCan said:**
> So the way things normally work, Grub2 needs both an MBR and a boot partition inside a linux OS.

If you set up Xubuntu in a partition on sda and use it to install Grub2 to the MBR of sda you are there. You just need a small partition for Xubuntu, say 5GB, unless you are going to use it for some other purpose than booting. You do not need to install any other Grubs anywhere.

Then, you can install new OSs all over the place as you like, including on sda, PROVIDED YOU DO NOT install Grub again, at least not to sda. Unfortunately, I think the Ubuntu installer does not allow you not to install Grub somewhere (d'oh) so you're best to install it to the OS partition itself (which will never be used).

Each time you install a new OS you would need to reboot into Xubuntu and run [COLOR="Navy"]sudo update-grub[/COLOR] to add it to the Grub menu.

This isn't the only way to do what you need but it is relatively easy.


Now, fedora 15 is a little interesting (it uses grub legacy by the way) and I advice not installing Grub at all (Anaconda lets you not install grub). Then reboot Xubuntu and install LVM which will facilitate Grub detecting fedora:
[COLOR="navy"]sudo apt-get install lvm2
sudo vgchange -ay
sudo update-grub[/COLOR]
and you will see fedora being added to the menu.

Grub does not need installed to both the mbr and a boot partition. Grub is installed to [COLOR="red"]**either**[/COLOR] the mbr or a boot partition. I recommend it be installed to the mbr.

Certain components of grub are installed to a couple directories on your linux partition. The part installed to the mbr doesn't do much more than hand off the process to the right partition for the rest of the files. The boot process is then handed off to the desired os based on your choice or grub defaults.

The grub-mkconfig process that runs from update-grub in ubuntu uses scripts from the grub directories to look for other os's to offer for boot options. This should find your os on sdb, whatever it is. When you install Fedora you might as well not have it install the boot loader. For some reason grub is different in Fedora than it is in Ubuntu flavors. An important difference is that when a kernel is updated in ubuntu, grub-update is automatically run to ensure display of the new kernel at the next boot. Fedora makes you remember to do this yourself using grub-mkconfig. 

One linux distro will have the "controlling" grub. It works best for that to be an ubuntu flavor. You do still have to remember to run update-grub from that controlling grub distro when a kernel changes for other installed distros. The controlling distro should be your most used distro. This all relates to added grub complexity induced by having more than 1 linux distro and my description is just for clarity given that you will have more than 2 OS's.

---

### Post by FormatSeize on 2011-09-01
Thanks everyone!

---

### Post by Bucky Ball on 2011-09-02
> **FormatSeize said:**
> Thanks everyone!

That's fine, but what fixed your problem? Please share. I'm assuming Boot-Repair, great little tool that is. ;)

---

