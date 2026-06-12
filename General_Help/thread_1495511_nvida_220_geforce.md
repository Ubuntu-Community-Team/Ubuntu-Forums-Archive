---
title: "nvida 220 geforce"
date: 2010-05-28
forum: General Help
---

### Post by mick463 on 2010-05-28
Hi there i have a nvida geforce gt 220 i tried to put it in my ubuntu system which was running fine of the on board vga before i put it in,and all i got was a black screen i know the card works as i have tested it on my windows machine. I have tried t0 change the boot file buy putting <option> at the end of a line in the grub file then did a grub-update but it did not work.I have given up on this card and gotten used to the fact that i have to buy another one can someone please tell me a card that works in ubuntu with no worries at all all it has to be is pci e don,t care if it is last years card. Thank you.

---

### Post by cryptotheslow on 2010-05-28
The GT 220 is supported by both the open Nouveau driver and NVidia's own proprietary driver.

There maybe a setting in the machine's BIOS to tell it to use the PCIE graphics over the onboard one.

When you say you get a black screen - do you even see the machine POST information when you start up?

If you do, try holding down the left shift key as it boots up and a question will pop up about using graphical boot - try non-graphical GRUB. If you can get to the GRUB menu that way you can try adding some boot options.

---

### Post by instinct46 on 2010-05-28
I know this might be a silly question but when does the black screen appear?? when computer boots, or when ubuntu boots.

---

### Post by mick463 on 2010-05-28
LOL I get the graphics card information and a blinking curser in the top left of the screen.
Also i know the bios sees it as i have been in the bios and tried auto and pci e settings.And i confirmed this with trying to put ubuntu on a windows machine that had the card working perfectly.This is the site that i have tried as it seems to have the same error that i have been having.

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Tried this but to no avail but it did allow me to get the live cd running and i found the driver for the card in hardware devices but when it told me to restart it would not start again so i am at a loss.

---

### Post by instinct46 on 2010-05-28
It could be a Nvidia driver problem, I don't know how you'd switch to an older version if you can't get access to your desktop though, suppose you could place LiveCD in and enter rescue mode, and when in the shell supposing your using a LAN internet connection, lynx to the nvidia website and download it from their... but through my past attempts at this results in an epic failure but when I tried to get back into the system it told me it failed and allowed me to switch to a standard driver, not good for gaming but may give you access to your Xserver

---

### Post by mick463 on 2010-05-28
It has never run at all but i think it might be the card its self as it should have run even without any drivers at all which it wont do so do you know of any cards that work so i can go and get one tomorrow morning and i can then at least get my ubuntu up and running.

---

### Post by instinct46 on 2010-05-28
I recently bought this card ATI HD 4550, its not nvidia but its was £40 with hypermemory. Initially 512mb but can be overclocked without strain to 1GB, I bought mine from maplins works perfectly with both my Ubuntu and Slackware

---

### Post by cryptotheslow on 2010-05-28
I had the same problem with my GTS250.

To get it to boot with the free Nouveau driver I had to use the nomodeset boot option.

After installing the driver from the Hardware Drivers section, nothing I did would get it to work correctly.

So - I deleted my /etc/X11/xorg.conf file and rebooted to go back to the Nouveau driver (nomodeset boot option again).

Then grabbed the driver installer file from the NVidia site and followed the steps in post #10 on this thread:
[http://ubuntuforums.org/showthread.php?t=1470343#10](http://ubuntuforums.org/showthread.php?t=1470343#10)

The crucial step seems to be blacklisting the Nouveau driver.

Now all is working well.

---

### Post by mick463 on 2010-05-28
The ony splash screen that i can get is the one off the live cd.I cant use the command that you said that command only works for me when i boot into the live cd and all the changes i make there make no difference to the main OS at all.

---

### Post by cryptotheslow on 2010-05-28
OK - have you tried booting the installed OS and holding down the left shift key from when your machine POSTs?

This should give you the option to use non-graphical Grub, where you should be able to add the boot option as required.

Alternatively, if you can boot to a usable desktop with the live CD, you should then be able to mount the hard drive with the install on it and remove the /etc/X11/xorg.conf file to revert that installed version to using the Nouveau driver - then you should be able to follow those commands when you boot into it.

---

### Post by mick463 on 2010-05-29
> **cryptotheslow said:**
> OK - have you tried booting the installed OS and holding down the left shift key from when your machine POSTs?

This should give you the option to use non-graphical Grub, where you should be able to add the boot option as required.

Alternatively, if you can boot to a usable desktop with the live CD, you should then be able to mount the hard drive with the install on it and remove the /etc/X11/xorg.conf file to revert that installed version to using the Nouveau driver - then you should be able to follow those commands when you boot into it.

tried all of that holding down shift dosent work and when i mount my system in the live cd i do not have the permissions to change anything.

---

