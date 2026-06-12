---
title: "Cant install drivers"
date: 2011-08-04
forum: General Help
---

### Post by manor9906 on 2011-08-04
i am using ubuntu 10.04, im fairly new to this so it might be an easy fix or not please help!! i am trying to install a driver for my acer tablet (using wine), i downloaded the driver with no problem extracted files and when i go to install it say it is preparing installshield then after a few seconds it says preparing to install as it gets about 25% it just quits and closes with no error message or anything. if it finished installing i cant find it and when i try again to install same thing. i might not be doing this right so please help..

---

### Post by gordintoronto on 2011-08-04
Wine is not useful for installing drivers. In the simple case, devices "just work" in Linux. If that's not true, it can be very painful; you need to Google the exact model code for your device, along with the word "linux".

---

### Post by xdominex on 2011-08-04
gordintoronto is right; WINE will not work for installing drivers. WINE accesses hardware through Ubuntu; Ubuntu does NOT access hardware through WINE. Therefore, drivers installed in WINE are useless. WINE tells Ubuntu what it wants from the hardware, and Ubuntu interacts with the hardware to (hopefully) get the job done.

What do you need a driver for? Perhaps I/we can help you figure out how to get your hardware working as it is supposed to.

With regards,
XDomineX

---

### Post by pqwoerituytrueiwoq on 2011-08-04
Here are some drives you may need maybe you will be lucky and have what you need here hopefully you don't need a ethernet/wireless driver

Video Drivers
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get udate;sudo apt-get upgrade
```
HP Printer drivers:
```
sudo add-apt-repository ppa:hplip-isv/ppa;sudo apt-get udate;sudo apt-get upgrade
```

---

### Post by manor9906 on 2011-08-23
thank for the help... i need a driver because my acer tablet has acersync and with most devices when u plug it in (via usb) it will recognize new device and instal drivers or program right from device... well acersync which allows me to move data from my computer (pics music etc.) to tablet doesnt come on the tablet itself it has to b downloaded from acers website... i also found on acer forums that this is a common problem that some have fixed ([http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html](http://www.acertabletforum.com/forum/acer-iconia-tab-general-discussions/129-connecting-via-usb-linux-ubuntu.html)) that is the thread but i am not sure how to do this as i am new i dont understand the lingo very well yet...

---

### Post by Mark Phelps on 2011-08-24
Wish you the best of luck with your Tablet.  I used to use Linux on my Tablet, but when they upgraded Ubuntu a few years back, the new kernel version would no longer detect the special keys, and screen rotation would no longer work.

Unfortunately, as you discovered, you can NOT use Windows drivers with Linux.  So, for me, that meant abandoning Linux on the tablet and going back to MS Windows -- where all the drivers worked.

---

### Post by xdominex on 2011-08-26
Ok, what lingo specifically do you not understand from that thread? It is an extremely well-written tutorial that should be pretty easy to follow, so I have high hopes of getting this working for you! I'll list a few things out for you in case it'll help you out, but please let me know anything else I can explain.

"terminal": a terminal is a program that provides a method of running commands through a "command line interface." This essentially means you don't use a mouse or pretty pictures, but CLI is very extremely useful for situations like yours. To access a terminal, press Alt+F2, type "gnome-terminal" (without the quotes), and press enter. A terminal should then appear in a window for you to use.

"file editing": Ubuntu (along with every other linux) runs according to contents of files, most of which are text-based. In step 7 he says, "Use the editor of your choice; mine is nano." He is simply referring to using a text editor. nano happens to be a CLI program, but if you're like me, you prefer the mouse and pretty presentation of a GUI (graphical user interface) over a CLI program (though I definitely make extensive use of CLI for other tasks). If so, use gedit instead. Whenever he has a line that starts with "sudo nano," press Alt+F2, paste in the line he has except with **gedit** where he has **nano**. I'll help you out by reposting all of the lines for you to make sure you see exactly what I mean.[INDENT]From step 7: ```
sudo gedit /etc/udev/rules.d/51-android.rules
```From step 9: ```
sudo gedit /etc/fstab
```From step 10: ```
sudo gedit /etc/fuse.conf
```From step 11: ```
sudo gedit /etc/group
```[/INDENT]"mount point": a mount point is a place in the file system where a drive or other file system of some kind is placed for access to its contents. In step 8, he has you creating this location and making sure that YOU are the owner of this location instead of "root." Ownership of this location is necessary to allow yourself to freely browse and use anything mounted at that location. In step 9, he has you adding the mount point to fstab. fstab is a file located in the /etc folder, and it controls the automatic mounting of (primarily) network locations and file systems. By following his instructions, you will set up the mounting to be handled automatically by Ubuntu whenever you plug in your tablet (I believe).

Last of all, please note that in step 7 you will have to replace **0502 **with whatever the vendor ID number for YOUR Acer happens to be. Step 6 explains how to find that your vendor ID for you to use in step 7.

If there's anything else you need explanation of or help for, let me know. I hope I have been helpful!

---

