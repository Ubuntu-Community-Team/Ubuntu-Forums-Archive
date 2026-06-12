---
title: "Adding Windows XP to GRUB and remove Windows 7 bootloader"
date: 2009-11-03
forum: General Help
---

### Post by sansa dude on 2009-11-03
Hi,

I have the Ubuntu Netbook Remix, Windows XP and Windows 7 on my Dell mini 10. When I start the computer, it goes to GRUB, and has the option for Ubuntu and Windows 7, not XP. When I choose windows 7 I goes to its own boot loader and the has windows xp after it with it's boot loader. So basically I have to go to 3 boot loaders for windows xp to start. What I would like to do is have them all on grub and as I click on one it starts booting that OS instead of taking me to another boot loader. 

I have done something like this on my other laptop with windows 2000 and ubuntu 9.04, but i don't remember how to do it, i know there is a menu.lst file i have to edit.

So can some one help me out with this?

Thanks so much in advance!

---

### Post by FallenArms on 2009-11-03
As far as I understand it, GRUB does not actually boot a Windows system.  What it does is, it loads the Windows bootloader (yes, they have one), which then lets you pick between any Windows systems you have installed.  Since GRUB can't load a Windows OS, you have to use that secondary bootloader to choose which one to load.

---

### Post by sliketymo on 2009-11-03
> **sansa dude said:**
> Hi,

I have the Ubuntu Netbook Remix, Windows XP and Windows 7 on my Dell mini 10. When I start the computer, it goes to GRUB, and has the option for Ubuntu and Windows 7, not XP. When I choose windows 7 I goes to its own boot loader and the has windows xp after it with it's boot loader. So basically I have to go to 3 boot loaders for windows xp to start. What I would like to do is have them all on grub and as I click on one it starts booting that OS instead of taking me to another boot loader. 

I have done something like this on my other laptop with windows 2000 and ubuntu 9.04, but i don't remember how to do it, i know there is a menu.lst file i have to edit.

So can some one help me out with this?



Thanks so much in advance!


Here is some good information on grub2:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by wildweathel on 2009-11-03
The basic problem is that Grub knows how to boot many things: linux, hurd, xen, grub, and other bootloaders.  But, it doesn't know how to boot Windows. Grub is limited to starting something called the Windows Partition Boot Loader (PBR).

It appears that Karmic isn't finding the Windows XP PBR.  This is because Windows XP doesn't one anymore! Vista overwrote it to install its own bootloader.  Thankyou Microsoft.

Gory details are here.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

But, the bottom line is that Karmic's grub2 can't have multiple options for multiple Microsoft OSes unless you work some magic with the Windows configuration.  Unfortunately I have zero experience here--I left Windows for greener pastures way back in 2003, and I've never admined a Windows system later than Windows 98.

But, I hope that info helps point you in the right direction.

---

### Post by sansa dude on 2009-11-03
OK so basically unless I do something with the windows boot loaders, there is nothing grub can do? Not even to add Windows XP to the Grub menu? before I installed Ubuntu I had to use windows 7's boot loader to boot into windows xp. so I guess grub just points me into the direction of where to boot. 

I don't know if this helps or not, but when Grub comes up it says " Windows 7 (loader)  (on /dev/sda1) "
I believe windows XP is on /dev/sda2 so is there a way i can add that to the boot menu? 

I ran the automatic grub update from the Grub guide as suggested above and it added nothing new.

Thanks for the help!

---

### Post by wildweathel on 2009-11-03
Yes.  It might end up not working or booting Windows 7's bootloader, but you can try it.  The file you want is /etc/grub.d/40_custom .  Pretty much all of the documentation is here: [http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211) .  It's a little hairy, though.

Good luck.

---

