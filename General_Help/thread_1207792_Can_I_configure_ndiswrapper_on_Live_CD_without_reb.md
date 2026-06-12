---
title: "Can I configure ndiswrapper on Live CD without rebooting?"
date: 2009-07-08
forum: General Help
---

### Post by Fleshtone on 2009-07-08
Hello All,

I've been trying to repair my Windows XP master boot record, which I probably damaged while playing with my GRUB settings.  

I'd like to follow the advice I found [here]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/"), which involves booting to the Ubuntu live CD and activating the universal repository and installing an app called ms-sys.

To get use of my linksys wifi card, I need to install the windows driver through ndiswrapper and blacklist the resident drivers.  That much is doable, but the problem is I'm doing it from the live CD, and so can not reboot to get the driver changes to take hold.  I have not found any instructions that do not mention rebooting before you can use your newly installed windows drivers.  Does anyone know of a way to get the drivers working without a reboot?

Thanks!

---

### Post by prshah on 2009-07-08
> **Fleshtone said:**
> 
To get use of my linksys wifi card, I need to install the windows driver through ndiswrapper and blacklist the resident drivers.  That much is doable, but the problem is I'm doing it from the live CD, and so can not reboot to get the driver changes to take hold.  

If you need a reboot just for the blacklist, you can just "modprobe -r" (remove modules) the relevant networking modules, without the need for a reboot. Nothing else requires a reboot; so, probably```
[s]sudo modprobe -r linksysmodulename[/s]
sudo modprobe -r bcmxx
sudo modprobe ndiswrapper
``` should work fine (assuming that you have performed ndiswrapper preliminaries). Please use the correct name in place of bcmxx.

---

### Post by Fleshtone on 2009-07-08
Thanks for the answer.  Just to clarify:  Why am I removing the linksys module?  Shouldn't I be removing the modules already running (in my case, bcm43xx et al.), in order to let the linksys driver be used?

Or, as is usually the case, am I missing something:p

---

### Post by prshah on 2009-07-09
> **Fleshtone said:**
> running (in my case, bcm43xx et al.), 
Or, as is usually the case, am I missing something:p

Nope, you're not missing anything; if anything is missing, it's my marbles.

You are quite right, you have to remove the bcm modules, not the linksysmodule, and I have accordingly corrected my previous post as well.

Please use the correct module name in place of bcmxx.

---

### Post by Fleshtone on 2009-07-09
Thanks for the help!  I could not figure out how to find the module names, everything came up "module not found".  However, I punted and schleped my desktop and monitor over to the router and plugged in the ethernet cable.  So that problem is solved, or detoured, as it were.  Thanks again.

It's amazing how many hurdles need to be passed on the way to solving a problem.  I'm a tinkerer, and so I've broken this machine many times.  This one is a doozy though.  I keep digging myself deeper with every attempt at digging out.  Now it looks like I've hosed my Windows partition completely, while trying to get it to boot again.  Just about the only thing I need Windows for is to sync my ipod touch!  But that little thing alone keeps me from going linux-only.

---

