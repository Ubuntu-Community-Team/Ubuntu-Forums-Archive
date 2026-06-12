---
title: "Installing Plop - Boot Manager?"
date: 2011-05-24
forum: General Help
---

### Post by djb6 on 2011-05-24
I need help with this.  I'm interested in trying out the Chrome OS but I don't have a laptop that will allow me to boot from a USB drive.  I did some research and learned that I can use this program to have the computer boot from the USB but I don't know how to install this using Ubuntu 11.04.  If anyone has any time tonight, is there any way that one could write the instructions for how to install this program in a simple way so that I can understand.

And yes, I realize that if I can't install this, maybe I shouldn't be messing with it, but I have a laptop that if anything disastrous happens to, I can just wipe it and start over so it doesn't really matter.

Thanks!

Here is the link for the website: [http://www.plop.at/en/bootmanager.html#intro](http://www.plop.at/en/bootmanager.html#intro)

---

### Post by linuxinstalledfromhdd on 2011-05-24
Yes, I see what you want to do.  You want to create a live bootable USB of Ubuntu to boot from..

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by djb6 on 2011-05-24
Thanks for the quick response.  That is what I'm interested in, other than making a bootable USB for Chrome OS, not Ubuntu.  I have a live CD for Ubuntu and my laptop can boot from the CD without any problem.

Anyways, I was looking at the website for Plop and here is what I don't understand:

> Warning Linux users: Install LILO or GRUB to the boot sector of your Linux instead of the Master Boot Record (MBR). The Plop Boot Manager is not a Linux loader and cannot start Linux without LILO, GRUB, Syslinux and similar!

and

> The install program
Install program menu
Harddisk install using Floppy with a disk image
Harddisk install using CD with an ISO file
Harddisk install using DOS
Harddisk install using Windows boot menu (2K, XP, VISTA, Win7)
Harddisk install using Syslinux, Isolinux, Pxelinux (Network)
Harddisk install using LILO
Harddisk install using GRUB

That list is a lot of choices I could make and I'm not sure which one to choose.  I'm thinking the last one, the one with GRUB.  When I follow that link, I get this:
> Download the current boot manager plpbt-5.0.12.zip. Extract it to get the boot manager install program. You find the install program plpinstc.com in the install directory.

Copy plpinstc.com to /boot.

You have to choose the correct root settings in menu.lst for your system.
The following is an example

title Plop Boot Manager Install
root (hd0,0)
kernel /boot/plpinstc.com

When you reboot, you should be able to choose the install program from your grub menu.

Can anyone help me understand all this?

---

### Post by linuxinstalledfromhdd on 2011-05-24
[http://cinderbox.net/2011/05/13/how-to-install-google-chromium-operating-system/](http://cinderbox.net/2011/05/13/how-to-install-google-chromium-operating-system/)

Does that help?

---

### Post by djb6 on 2011-05-24
Yeah that all helps with that actually installing, but I can do that.  What I need help with is putting plop on this computer so I can in fact boot from a USB drive?  Right now, I can't because my computer is too old for that.

---

### Post by linuxinstalledfromhdd on 2011-05-24
I'm sorry, I didn't quite understand that you system was that old.  My bad. :lolflag:

---

### Post by djb6 on 2011-05-24
Haha no problem.  Thanks for the help anyways.  Again, if anyone can help me intrepid this directions, I would be very grateful.

---

### Post by tgalati4 on 2011-05-24
I found a chromeOS live CD, but it was built on SUSE linux and it was kind of buggy at the time.  Search around, you may find other LiveCD's of ChromeOS.  That would be easier to play with than trying to get Plop to work.  Be careful because Plop overwrites your MBR and can mess up booting from your hard disk.  It doesn't always work because some machines are crippled and the USB devices aren't found or enumerated properly.

You can get 90% of the chromeOS experience by installing google chrome web browser, logging into your gmail account (you need one to use the web documents) then start playing with the web applications available.  Since everything is stored in the cloud, you don't need to worry about locally storing your documents.

---

### Post by djb6 on 2011-05-25
Yeah that was a fake version that came out a few years ago.  The SUSE version that is.  As far as messing up my MBR, I actually found a live CD of the Plop so I can just use that instead.  

ChromeOS doesn't have a live CD yet.  Hopefully that will come out at some point, but as of now, no live CD.  I think I've worked it all out though so that I can try it out.  Thanks for all the help.

---

### Post by mike555 on 2011-05-25
If your computer boots a cd , just burn plop on a cd (as a an image ) ......... it will start and give you the option to boot usb .

you will need the .iso version of plop.

---

### Post by djb6 on 2011-05-25
Thanks!  I figured that out and I think I have it working now.  I'm marking this as solved hoping it work. :)

---

