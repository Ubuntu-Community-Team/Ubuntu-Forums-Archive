---
title: "Flashing colors on Ubuntu 9.10 boot, HELP!"
date: 2010-09-04
forum: General Help
---

### Post by brovah on 2010-09-04
Hello,
 
about a year ago I installed Ubuntu 9.10 next to Windows XP as a dual boot. Everything worked fine and I only used it for certain purposes, before leaving it alone for several months. Now I want to start working with Ubuntu again, however something weird happens after I choose any version in normal mode from Grub.
 
In Grub I can choose from different 9.10 versions (updates), each with a normal and recovery mode. The recovery mode and its command line work fine; I can even access my files. But I want to work in normal mode.
If I choose this, regardless of what version it is, then I see the small Ubuntu logo and it seems to walk well into the login screen. However, whenever the login screen is supposed to show, I get the following screen:
 
[IMG]http://img534.imageshack.us/img534/8947/ubu1.jpg[/IMG]
 
 
Just a bunch of vertical colored flashing bars all over my screen. The "Not-Optimum-mode" message in the middle is something my TFT-monitor does, as I connected my old CRT-monitor afterwards, showing me the exact same thing, except for that message.
 
Once this screen pops up, I do get the usual tribal drum sounds, which occur if the login screen shows up.
 
Can somebody help me fix this, please?
Some background information: I am not an expert on Linux, my graphics card is an NVidia GeForce 6600 and I recently replaced my CMOS battery.
 
Thanks in advance!
 
 
Question on the side: If I upgrade to the latest Ubuntu version, might this fix my problem and if it does, will all my data still be there?

---

### Post by Rubi1200 on 2010-09-04
Try booting with the nomodeset parameter and see if it makes a difference:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

You can do this when GRUB comes up by selecting "e" for the kernel, finding the line that ends with ```
ro quiet splash
``` removing quiet splash entering the parameter and then "Ctrl" + "x" to boot.

---

### Post by brovah on 2010-09-04
> **Rubi1200 said:**
> Try booting with the nomodeset parameter and see if it makes a difference:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
 
You can do this when GRUB comes up by selecting "e" for the kernel, finding the line that ends with ```
ro quiet splash
``` removing quiet splash entering the parameter and then "Ctrl" + "x" to boot.
 
 
I tried this, but with no effect. Note that I am not booting from a CD, but that I reserved some disk space for Ubuntu in Windows and installed it from there.

---

### Post by Rubi1200 on 2010-09-04
Sorry, I am a bit confused now.

> I installed Ubuntu 9.10 **next** to Windows

> I reserved some disk space for Ubuntu **in** Windows and installed it from there

Is this a regular install to the drive or a Wubi install?

---

### Post by brovah on 2010-09-04
> **Rubi1200 said:**
> Sorry, I am a bit confused now.
 
Is this a regular install to the drive or a Wubi install?
 
 
I do not believe it is a Wubi install, i.e. I do not recall encountering that word when I first got Ubuntu. I downloaded an .ISO from the Ubuntu site and mounted it with Daemon Tools and installed it while in Windows. When I boot, I can choose between starting XP or Ubuntu.

---

### Post by Rubi1200 on 2010-09-04
Do you have an Ubuntu CD, or can you make one, to use as a LiveCD?

If yes, boot the computer choosing to try _not_ install.

Then post the results of the bootscript linked to at the bottom of my post.

Thanks.

---

### Post by brovah on 2010-09-04
> **Rubi1200 said:**
> Do you have an Ubuntu CD, or can you make one, to use as a LiveCD?
 
If yes, boot the computer choosing to try _not_ install.
 
Then post the results of the bootscript linked to at the bottom of my post.
 
Thanks.
 
 
Okay, this may be a silly question, but then again this is entirely new to me. I can make a LiveCD, but can I use a DVD disc for that? And what exactly do I need to put on that disc?

---

### Post by Rubi1200 on 2010-09-04
Yes you can also use a DVD disc. You need to burn the .iso image you downloaded from the Ubuntu site and use a burning program to burn it to the DVD. 

I don't use Windows so I cannot tell you which one to use, but a quick Google search should find something if you don't already have one installed.

Burn at the lowest possible speed for best results.

---

### Post by brovah on 2010-09-04
> **Rubi1200 said:**
> Yes you can also use a DVD disc. You need to burn the .iso image you downloaded from the Ubuntu site and use a burning program to burn it to the DVD. 
 
I don't use Windows so I cannot tell you which one to use, but a quick Google search should find something if you don't already have one installed.
 
Burn at the lowest possible speed for best results.
 
 
I just so happens I did exactly just that this afternoon. :D
 
However, I placed it in my DVD-drive and rebooted, but there were no options I could choose from that made it boot from CD. In other words, with the CD in I got the boot screens I always get.

---

### Post by Rubi1200 on 2010-09-04
> **brovah said:**
> I just so happens I did exactly just that this afternoon. :D
 
However, I placed it in my DVD-drive and rebooted, but there were no options I could choose from that made it boot from CD. In other words, with the CD in I got the boot screens I always get.
You need to go into BIOS and set it to boot from the CD/DVD drive.
Depending on your machine, it is usually something like F2 or F12. 
Do this as the machine is starting. Find the section for boot priority (something along those lines) and change the order.
Then try again.

---

### Post by brovah on 2010-09-04
> **Rubi1200 said:**
> You need to go into BIOS and set it to boot from the CD/DVD drive.
Depending on your machine, it is usually something like F2 or F12. 
Do this as the machine is starting. Find the section for boot priority (something along those lines) and change the order.
Then try again.
 
Already did that earlier this afternoon. The order is now: 1) CD-ROM - 2) Removable - 3) Hard Disk.
 
Still nothing.

---

### Post by brovah on 2010-09-05
Still not fixed. Anybody have any ideas?

---

### Post by brovah on 2010-09-05
Alright, after trying countless solutions, I decided to save my important files to a USB drive in recovery mode and install Ubuntu 10.04. Everything is back to normal now.
 
Thanks anyway for being so kind to help me out! :)

---

### Post by Rubi1200 on 2010-09-05
I am glad you managed to sort things out and sorry I wasn't able to offer more in the way of help.

But, sometimes, the course of action you took is the best solution.

:)

---

