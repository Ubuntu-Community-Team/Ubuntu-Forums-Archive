---
title: "Bootable external drive"
date: 2012-01-31
forum: General Help
---

### Post by lou002 on 2012-01-31
I'm not sure if this should go here or not; and I couldn't find anything else on it (if there is then I apologize)

I want to use Linux more, and expand my computer knowledge (a lofty goal I know) but I'm nervous to dual boot. I own an iPad and play World of Warcraft (till April), so Windows is important to me. I was thinking of giving only 5-10 gigs to run it but then I keep coming back to 'what if I need those gigs on windows, how do I get them back without messing up my windows install'

So a friend suggested getting an external drive and making it bootable. Well, I have Western Digital 500gb drive I'm not using for anything. So I had a couple of questions that I hope could find answers:

-Is it possible to make it bootable? As in use the OS just like any other computer, save things to the drive, etc?

-How do you do so? what's the easiest way? A friend suggested taking a CD and putting a distro on it (I put Ubuntu main flavor) and then installing to the USB drive instead of my internal drive

-What would happen I removed the drive from the USB port? Would I lose the ability to use my Windows stuff (even though the windows drive is built into the PC)

I know, I'm a noob and probably shouldn't touch this stuff; but how else can I learn?

I apologize if I don't make sense, I'm working on about 4-5 hours of sleep and an empty stomach but this thought was burned into my brain

---

### Post by oldfred on 2012-01-31
First does your computer BIOS let you boot from a USB port? Most systems in the last 5 years do. If so you can set BIOS to boot USB first and is not found it then uses the second choice or your internal hard drive.

But to make that work you have to install Ubuntu's grub2 boot loader to the external drive's MBR. Then Windows boot loader in the MBR of the internal drive is not modified.

The only way to install grub2 to the external drive is to use manual install or something else. The auto installs all assume you want to boot from sda (the internal in your case) and will install to sda.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by lou002 on 2012-01-31
> **oldfred said:**
> First does your computer BIOS let you boot from a USB port? Most systems in the last 5 years do. If so you can set BIOS to boot USB first and is not found it then uses the second choice or your internal hard drive.

I can go into boot options and select with to boot from. It's a Dell Inspiron 560, and i bought it in March.

I'm thinking maybe just using Wubi? This all sounds so complicated.

---

### Post by btindie on 2012-01-31
> -Is it possible to make it bootable? As in use the OS just like any other computer, save things to the drive, etc?There's nothing to stop you making an external USB disk bootable providing your BIOS supports it. That's actually how I do it on my laptop but then I can press F12 to get the boot menu and it gives me the option to boot of the USB disk which makes it easier. The downside is that USB is much slower than SATA but for general stuff I find it acceptable given the slowness of windows. On mine, windows is still using the entire internal HD, I just haven't got around to replacing it. Just keep putting it off as I'm happy with the external disk though that's quickly filling up as it's only small..

> -How do you do so? what's the easiest way? A friend suggested taking a  CD and putting a distro on it (I put Ubuntu main flavor) and then  installing to the USB drive instead of my internal driveThere's a couple of options. You can either burn the image to CD and boot from that or you can create a bootable USB stick to install from. You can do this manually, more for an experienced user, or use [UNetbootin]("http://unetbootin.sourceforge.net/") to create it for you. Providing you've got a big enough USB stick you could also create an overlay to allow you to save changes to that and just run off the USB stick. The other option is to do a WUBI install which installs it alongside windows in the NTFS partition but it can easily be deleted if you don't want it any more, the drawback is that it's not quite as fast.

> -What would happen I removed the drive from the USB port? Would I lose  the ability to use my Windows stuff (even though the windows drive is  built into the PC)That would depend on how you installed and configured your system. If your computer allows you to select the drive to boot from at POST then go for that. Just make sure that if you install Ubuntu on it's own drive that you install GRUB, the boot manager, into the same MBR and to to overwrite the windows MBR - though this can be recovered. You could always disconnect the SATA cable from your windows drive to avoid any problems when doing the install.

> I know, I'm a noob and probably shouldn't touch this stuff; but how else can I learn?That's how we all learn but just remember to have a backup of any important data in case you end up wiping your drive.

Your best option may be to do the WUBI install first just to get an idea of it as that may be the simplest option. If you want to test a full system and to get an idea of the performance then you may be better of installing the spare disk inside your computer and dual boot from that. You can configure the windows boot loader with [this]("https://wiki.archlinux.org/index.php/Windows_and_Arch_Dual_Boot#Using_Windows_7_Boot-Loader") guide.

---

### Post by btindie on 2012-01-31
> **lou002 said:**
> I can go into boot options and select with to boot from. It's a Dell Inspiron 560, and i bought it in March.

I'm thinking maybe just using Wubi? This all sounds so complicated.

If that's the case, disconnect your windows disk and install the other disk into the 2nd 3.5" tray and connect it to the 2nd SATA port. Boot from your Ubuntu install media and follow the default options about how to partition the disk and where to install the boot manager.

Once the install is complete, power off, connect the windows disk and power it back on. Go into the boot options and boot from the 2nd disk.. job done.

Your windows disk should still be the primary one it boots from.

---

### Post by lou002 on 2012-01-31
> **btindie said:**
> If that's the case, disconnect your windows disk and install the other disk into the 2nd 3.5" tray and connect it to the 2nd SATA port. Boot from your Ubuntu install media and follow the default options about how to partition the disk and where to install the boot manager.

Once the install is complete, power off, connect the windows disk and power it back on. Go into the boot options and boot from the 2nd disk.. job done.

Your windows disk should still be the primary one it boots from.


The windows disk is an internal disk drive and the computer is still under warranty until March or April. Maybe even later than that. I am not opening it up.

And the other drive is USB external that requires an AC adapter plugged into a wall to work.


Thank you for the advice, though. Going to mark this as solved and just use Wubi.

---

### Post by Christopher Marks on 2012-06-01
Hi! You can create a bootable Ubuntu Distro in USB using Ubuntu's Archive Manager or Ubuntu's USB creator. Just follow the steps available here [http://www.techyv.com/questions/create-bootable-ubuntu-distro-usb](http://www.techyv.com/questions/create-bootable-ubuntu-distro-usb)

---

