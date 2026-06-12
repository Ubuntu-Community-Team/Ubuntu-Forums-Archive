---
title: "Installed ubuntu 10.10 on new netbook, couple issues."
date: 2011-03-01
forum: General Help
---

### Post by bentomo on 2011-03-01
I'm new to linux pretty much entirely, I've used ubuntu before, mostly because it works when windows doesn't and I just got a new amd fusion netbook. The acer aspire one 522.

I have a couple issues, 2 with grub, and one with an amd watermark.

1. There are two ubuntus and two ubuntu memory tests in the grub, I can't see any difference between them, after I booted the first time into ubuntu and updated, I restarted and the grub gave me two ubuntus.

Can I remove the second one from the list? (not an issue I just want to clean it up)

2. I need to make windows 7 the default operating system, I've looked at other guides and I can't figure it out. I've tried menu.lst, and when I try grub.cfg I can't change the default.

Any suggestions? 

3. I installed the unofficial drivers for the wireless adapter and graphics card (6250 on fusion) and now everything is working fine with them, except I have the unremovable watermark in the bottom right corner that says "AMD Unsupported hardware"

How do I remove this?

BONUS question!
How do I tell ubuntu, this is my netbook, stop denying me access to my own computer and let me in that folder!

I can't access the root folder, and I'd like to do install things without ubuntu asking me for my password every time. I'm not worried about other people being on this netbook, no super valuable info, and not really anyone else is on it anyway.

Any way I could give it a master password and roam freely inside my netbook?

---

### Post by Bucky Ball on 2011-03-01
In answer to the bonus question: Yes, but changing settings as root can have disastrous results! It wouldn't take a user more than half a minute to change an important setting and break the install or setting as they are performing actions at root. Not wise but what you're asking can be achieved. 

You can open Nautilus as root and change permissions. In a terminal, type:

```
sudo nautilus
```This will let you right click and change folder permissions. A perfect example of why having every user as root is not a good idea!

For all things grub2 fiddling in 10.04 and on, you need Grub Customizer:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

As for the watermark no idea, sorry. ;)

Welcome and glad you seem to be enjoying Ubuntu ...

---

### Post by bentomo on 2011-03-01
Thanks for the grub manager, works great now.

The only thing left is the amd watermark, I can't figure it out. I've tried reinstalling the drivers and all, I think that ubuntu doesn't have support for the chipset yet.

---

### Post by Primefalcon on 2011-03-01
I tried 10.10 on the eeepc 901ha a while back, and had a **** load of trouble, with not being able to choose logins if I have one account auto logging in....... If I pressed escape so I could log in with an alternate (secure) account.... it'd just throw a lot of weird graphical **** and exit.....

So same day I just threw 10.04 back on it..... If they dont have that sorted by next LTS I'll be throwing either mint or OpenSuse on there instead

---

### Post by manticoretrader on 2011-03-13
w/ watermark: Install open source X11 drivers as mentioned here: [http://www.manticore-projects.com/content/en/software/guides/aspire522.htm](http://www.manticore-projects.com/content/en/software/guides/aspire522.htm) (do not forget firmware and KMS).

Best regards

---

### Post by jason.s on 2011-03-16
I am in the same boat using the same version of the Aspire One 522 netbook.  I looked at [http://www.manticore-projects.com/content/en/software/guides/aspire522.htm](http://www.manticore-projects.com/content/en/software/guides/aspire522.htm) and they mentioned updating the kernel version.  There was a "download fitted kernel config" link, but I'm not sure what to do with that.  Do I just overwrite the old config file?  I am a complete ubuntu noob (this is the first I have used it)... I apologize if that's a dumb question, but I can't find what a "fitted kernel config" actually is, but I am assuming I just need to replace the old config file with this one?

Also, when they say to do this:

"I use the open source driver x11-drivers/xf86-video-ati (from git  repository), which runs well supporting OpenGL, XV and suspend-to-ram.  In order to use this driver you will need kernel-2.6.38 (from  git-repository) and you need to install the IRQ microcode for  r6xx/r7xx/Evergreen Radeon GPUs from [x11-drivers/radeon-ucode]("http://people.freedesktop.org/%7Eagd5f/radeon_ucode/") and link it into the kernel:"

What do I do to install it? Just extract the files somewhere?

---

### Post by Bucky Ball on 2011-03-16
> **Primefalcon said:**
> ..... If they dont have that sorted by next LTS I'll be throwing either mint or OpenSuse on there instead

The next LTS release won't be until April 2012 so you have awhile to wait. ;)

---

