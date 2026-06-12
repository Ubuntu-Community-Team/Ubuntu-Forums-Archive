---
title: "Bootup Resolution"
date: 2010-06-03
forum: General Help
---

### Post by ibbill on 2010-06-03
My boot up resolution  10.4 Lucid is 640 x480 Any chance of changing this so I can see the whole boot menu have really read and looked around for help on this.

May be I am missing something. Really appreciate some help.

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Craigular.B on 2010-06-03
> **ibbill said:**
> My boot up resolution  10.4 Lucid is 640 x480 Any chance of changing this so I can see the whole boot menu have really read and looked around for help on this.

May be I am missing something. Really appreciate some help.

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

First you should find out what resolutions grub2 supports for you (assuming you have grub2; I'm not sure/don't remember how to change this in grub). When your menu is displayed press "c" to get to a grub> prompt and type ```
vbeinfo
``` and press Enter. It will display the resolutions grub2 can handle on your monitor. Press Escape (ESC) to return to your boot menu.

Now, you need to edit your grub file:```
sudo gedit /etc/default/grub
```

Then you'll look for a block of code like this: ```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
```

Uncomment (remove the "#") the last night of that block (GRUB_GFXMODE=....) and change the size to whatever you want it to be/found when you ran vbeinfo. Try to pick your monitor's native resolution to avoid stretching and pixelation. For example, on my Macbook Pro the native resolution is 1920x1200, so my code looks like: ```
GRUB_GFXMODE=1920x1200x32
``` (the extra x32 is for the color depth setting).

Finally, save that file and run ```
sudo update-grub
``` to get grub2 to recognize your changes. Reboot and you should be set.

---

### Post by Rasa1111 on 2010-06-03
mine does the same thing. still. lol
everything in Lucid is now perfect here, 
except the funky graphics at bootup. lol

Craigular~ thanks.. Im going to re-read your post about ten times and then maybe attempt it. lol
:)

---

### Post by abhot on 2010-06-03
regarding boot resolution i would suggest you visit this site
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by ibbill on 2010-06-03
Craigular.B Sir a tip of my hat to you. Thank you ever so much worked like a charm. Will mark this thread solved.

Can't thank you enough.

---

### Post by Rasa1111 on 2010-06-04
> **abhot said:**
> regarding boot resolution i would suggest you visit this site
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

All fixed! thanks!

 I didnt quite get an instruction or two in craigulars post,
so I didnt bother with it.. But this link helped! 

 well, It was supposed to make the splash screen fixed resolution,
but instead it just made it disappear for good..
(and I did option one)
I dont know..

Oh well, Id rather have no splash than a big fugly one. lol

 thanks mate!

---

