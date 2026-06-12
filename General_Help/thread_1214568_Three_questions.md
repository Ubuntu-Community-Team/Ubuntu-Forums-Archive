---
title: "Three questions"
date: 2009-07-16
forum: General Help
---

### Post by epizoan on 2009-07-16
Hello,
 
I am new to Linux and to Ubuntu. I have been wanting to learn Linux for quite some time. My three questions are;
 
1. How can I boot and log into my Ubuntu without the GUI. I don't wish to disable or uninstall GNOME, I only want to log into my install without the Desktop environment loaded. Using the GRUB options automatically installed I was able to boot into ROOT but not able to log in.
 
2. I share my laptop with my wife and I would like to be able to boot to GRUB from a USB or disc to acess my install. I want to restore the Vista bootloader so my wife and kids can not boot into my linux install without the thumbdrive or boot disc. Also I would like to set up my second laptop without a hdd bootloader and use only my USB to load into it. Is this possible? If so where can I find the information to help me succeed?
 
3. I would also like to condense my Ubuntu/Kubuntu/Xubuntu .iso's into one single bootable DVD for ease of use and install. I am sure this is possible but my lack of experience with Linux is putting a damper on things. 
 
I would appreciate any input anyone may have and I thank you for your time and help.
 
Epizoan

---

### Post by nothingspecial on 2009-07-16
For first see [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1187863")

As for the other 2 they sound possible but I`m not sure how. I might have a go this week.

---

### Post by bernied on 2009-07-16
> **epizoan said:**
> Hello,
 
I am new to Linux and to Ubuntu. I have been wanting to learn Linux for quite some time.
Welcome!
> **epizoan said:**
> My three questions are;
 
1. How can I boot and log into my Ubuntu without the GUI. I don't wish to disable or uninstall GNOME, I only want to log into my install without the Desktop environment loaded. Using the GRUB options automatically installed I was able to boot into ROOT but not able to log in.
This was historically done using runlevels. Startup applications/services are controlled in the /etc/rcX.d directories (where X is the numbers 0-6, or S). In these directories are links to the scripts in /etc/init.d. Links that start with an S start a service, those that start with K stop (kill) services. Runlevel 0 is shutdown, 1 is for emergency (superuser), 6 is restart, and S is startup. So there are 4 runlevels available for the user (2-5). Starting in any runlevel starts the links in /etc/rcS.d/ first, then those in the particular runlevel directory.

Anyway, you should be able to take one of those numbers for yourself, adapt it to your purpose (just remove the link to the gui, probably gdm), then create a grub boot entry to start in it, by adding an extra parameter on the kernel line. But first find out which one starts by default, and don't mess with that one. The command 'runlevel' will tell you (it is probably 2, as mine is).
 
> **epizoan said:**
> 2. I share my laptop with my wife and I would like to be able to boot to GRUB from a USB or disc to acess my install. I want to restore the Vista bootloader so my wife and kids can not boot into my linux install without the thumbdrive or boot disc. Also I would like to set up my second laptop without a hdd bootloader and use only my USB to load into it. Is this possible? If so where can I find the information to help me succeed?This is possible, but it is more than you need to do to achieve what you say you want.

You can change the grub config to:
- make windows the default (default)
- hide the menu (hiddenmenu)
- reduce the timeout (timeout)
If you did this, windows would start by default, and to start your linux you'd need to hit Esc at a critical time to get the boot menu. Have a look in /boot/grub/menu.lst for details.

If you really do want to boot off USB, you can install grub onto a usb stick (try the [grub manual](http://www.gnu.org/software/grub/manual/grub.html)). You can even partition a usb stick (use fdisk or gparted), so that it has a boot partition, but looks to a windows machine like a standard usb stick (except that it seems to be missing some space), just make the first partition a primary, and format it is FAT32.
 
> **epizoan said:**
> 3. I would also like to condense my Ubuntu/Kubuntu/Xubuntu .iso's into one single bootable DVD for ease of use and install. I am sure this is possible but my lack of experience with Linux is putting a damper on things. This is not so easy. These CDs use IOSLINUX to boot, and I'm not sure whether you can have multiple booting installs on the same media. You could check out Grub4Dos, which might be able to do it. But keep in mind that your DVD will be out of date in 6 months time.

But my advice would be to put an emergency install on your usb stick - I use slax for this. The advantage of this is that you can add stuff to it, for example any wireless drivers that you might need.

I haven't given you step-by-step instructions here, but hopefully enough keywords for googling. Ask for clarification.

You are jumping in the deep end - enjoy!

---

### Post by bernied on 2009-07-16
For question three, it looks like there now might be a relatively easy way to do this, using grub4dos. The main docs are here:
[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

It's not spelled out for you, but grub4dos can boot .iso images directly, so once you had made your usb device bootable using grub4dos, you would just need to add the .iso file, then add an entry for it in your menu.lst.

Though I wonder if some live-cds might have trouble, as the kernel might be looking for its files on a cd/dvd device ...

[EDIT]Sorry, I wrote too soon. You should read this before trying what I suggested:
[http://diddy.boot-land.net/grub4dos/files/map.htm#hd32](http://diddy.boot-land.net/grub4dos/files/map.htm#hd32)[/EDIT]

---

### Post by epizoan on 2009-07-17
Thanks for all the great advice. I didn't even think about using a USB initially for the installs but it seems a valid option for my personal machine. I wanted to keep the disc for other machines. I figured the disc would be good for at least a year, using the update client from the install to get the latest release. I plan on keeping an archive of releases from 8.04 on my TB for ease of access. The disc would be for portability and compatibility. 
 
I actually have one more question. I am working on learning file structure and figuring out Terminal commands and syntax right now. Can you provide me with a link(s) to helpful sites. I have google searched and 99% are walkthroughs for specific issues and it would take me forever to sort out usable commands and their functions. I am looking for a list of commands and such. I would resort to buying a book but I like the feeling of accomplishment with the hands on (dive in and figure it out) approach. The major problem is I have DOS and windows shell commands and syntax burned into my brain and I get frustrated. 
 
Thanks again,
Gavinzach

---

### Post by nothingspecial on 2009-07-17
See [[COLOR="Magenta"]here[/COLOR]]("http://gd.tuwien.ac.at/linuxcommand.org/") for a good beginners guide.

I`ve heard that it`s not learning linux that`s difficult, it`s unlearning windows that is the hard part.

---

### Post by bernied on 2009-07-17
Some links:
- [bash commands](http://www.ss64.com/bash/)
- [linux directory structure](http://www.debianadmin.com/linux-directory-structure-overview.html)
- [linux file permissions](http://www.hostingmanual.net/other/permissions.shtml)

---

### Post by epizoan on 2009-07-17
Thanks again everyone. I see I signed my post with my username from another forum... oops! Thanks for all the help.

---

