---
title: "Installation"
date: 2010-09-26
forum: General Help
---

### Post by johnbockbank on 2010-09-26
I have installed an external drive on my Windows 7 PC and therefore feel able to try to set up a dual boot with another operating system, and Ubuntu is the obvious first choice: however on the Ubuntu site the only options avaiable seem to be to install to a stick or on a new partition on the Windows C: drive. I couldn't really fathom installing to a stick and nothing seemed to run off the DVD to which I wrote the .iso file. I most definitely do not want to alter the C drive.
 
Seems to me it would be a good idea to have the option to install to any drive partition of one's choice. My son-in-law who uses Linux a lot in work suggested a web site explaining how to install Linux on an external drive, but that entails opening the PC and disconnecting the C drive. I assume that is because otherwise I would lose the Windows installation. My interest in PCs is most definitely directed towards systems and software, not hardware so I don't trust myself poking aound inside.
 
There is presumably an explanation of why there is no simple way to ty out Ubuntu etc. but I can not find any explanations and would be grateful for a pointer about where I should look.

---

### Post by Quackers on 2010-09-26
When you wrote the iso file to a disc did you select "burn image"? If you just write the files to a disc it will not work. When booting from the Ubuntu disc you should get the option to "try out Ubuntu". This is an option that does not change anything on your system at all. It just lets you see how Ubuntu looks and works.

---

### Post by Topsiho on 2010-09-26
In Ubuntu (and all other Linuxes) there is no such thing as a C:\ disk.
Windows is installed in one or more partitions of one disk, usually, which partitions are called C:\, D:\ and so on.

If you install Ubuntu, you should install Ubuntu in one or more partitions of its own, on the same, or in more than one disk.

As probably Windows is installed so that it uses all the disk, you should first make room for Ubuntu, using a partition manager. I advise you to do so with the partition manager that comes with Windows. Not that it is better, but my experience is that you have less chance that after the installing of Ubuntu, Windows doesn't boot any more. Windows seems to remember the previous situation, and panics when it doesn't find it. That is how I interpret things.
Don't forget defragmenting first, and backing up all your precious files.

To make a long story short, Google "Howto install Ubuntu", and you'll find among other suggestions:

[http://seogadget.co.uk/the-ubuntu-installation-guide/#install-from-CD](http://seogadget.co.uk/the-ubuntu-installation-guide/#install-from-CD)

and read that first leisurely.

Hope this helps :)

Topsiho

---

### Post by snowpine on 2010-09-26
It is not, strictly speaking, necessary to disconnect your internal HDD when installing to an external HDD. Many tutorials recommend this as a safety mechanism so that inexperienced users do not accidentally overwrite their Windows partitions and/or Windows bootloader.

If you are 100% confident in your ability to correctly install both Ubuntu and the GRUB bootloader to the correct partition of the correct drive, and you have a full backup of everything on the internal HDD, then you may choose to skip the "disconnect internal HDD" step at your own risk. 

If you are not confident disconnecting your internal HDD, and you are also not confident with the advanced features of the Ubuntu installer, then the safest option is to burn a "Live CD" and try it "with no change to your computer" as a learning experience until you are more familiar with Ubuntu.

Good luck!

(edit) ps I would also advise caution following some random how-to your son-in-law found on the internet. Be appropriately cautious following any 3rd party tutorial that is not part of help.ubuntu.com or wiki.ubuntu.com!

---

### Post by dirghrabadia on 2010-09-26
> As probably Windows is installed so that it uses all the disk, you should first make room for Ubuntu, using a partition manager.

I would use GParted LIVE CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)), make space for Ubuntu, and then install it from an Ubuntu LIVE CD.

---

