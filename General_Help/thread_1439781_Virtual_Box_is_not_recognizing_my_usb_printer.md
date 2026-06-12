---
title: "Virtual Box is not recognizing my usb printer"
date: 2010-03-26
forum: General Help
---

### Post by monicamaria on 2010-03-26
Please help!  I am trying to make my Lexmark P4350 printer work so I downloaded Virtual Box on my laptop and installed Windows XP on it.  This printer worked great with XP on another computer.  I have done all the updates to XP and it seems to be working just fine but when I go to the printer set up, it is not showing up.  I have tried it where I plug in the printer while Virtual Box is running, but it didn't seem to make any difference.  When I plug the printer into the usb port, Ubunto starts searching for the drivers but the Virtual Box doesn't. :confused:

I would greatly appreciate any help.

Monica

---

### Post by howefield on 2010-03-26
Just to check, this is the PUEL version of Virtualbox from the website that you installed, and not the OSE version in the UBuntu repository ?

---

### Post by philinux on 2010-03-26
[http://www.virtualbox.org/manual/ch02.html#id2515239](http://www.virtualbox.org/manual/ch02.html#id2515239)

---

### Post by QIII on 2010-03-26
The reason howefield asks is this:

There is no USB support in the OSE version, but there is in the PUEL  version.

---

### Post by monicamaria on 2010-03-26
Thanks for the quick replies.  I went back to the website to see and I think I downloaded the PUEL version.  It seems like I clicked the download that said it was free and for personal use.  Is there a place where this information is listed in Virtual Box?  I was looking on the details tab in VB and saw where it shows 1 active usb port and Lexmark 4300 series is listed, if that helps.

Monica

---

### Post by ajgreeny on 2010-03-26
You must make sure you enable usb support in the properties of the virtual machine you produced by clicking on it in the left hand panel and selecting the properties you need and want from those showing in the right hand pane..

---

### Post by monicamaria on 2010-03-26
the usb ports are enabled in the settings details.  I have an usb optical mouse connected and it is working in both VB and in XP when it is running.

---

### Post by macogw on 2010-03-26
Mice work regardless of whether USB stuff is setup, I believe (would be difficult if they didn't!)

---

### Post by HotShotDJ on 2010-03-26
> **monicamaria said:**
> the usb ports are enabled in the settings details.  I have an usb optical mouse connected and it is working in both VB and in XP when it is running.USB Keyboard and Mouse are both virtualized in VirtualBox... in other words, the guest OS will not see them as USB devices, so of course, they work straight away.

For other USB devices, VirtualBox must hand control of the hardware (such as the printer) from the host OS to the guest OS.  Most USB devices can be used either by the host or the guest... not both -- keyboards and mice are the exception to this rule. There are a number of ways activate a USB device for your virtual machine one way is to go to Devices --> USB.  Select your device to activate.  Windows should now detect it.  Just install the drivers (if necessary) and you'll be all set to use your USB device in the guest OS.

---

### Post by monicamaria on 2010-03-26
I went to  Devices --> USB and the Lexmark was listed but I could not highlight it or check the box.

---

### Post by slellis on 2010-03-27
Hi, guys,

I'm having the same problem.
My VB is installed on a Ubuntu Karmic Koala host system and the guest system is a XP.
All devices are recognized by USB port on XP, but my EPSON C92 printer.
When the USB icon (down in the VB bar) is clicked with the right button, the "Epson USB printer" is listed among other devices, but it is greyed and has no checkbox.

Please help.
Thanks in advance.

Lellis

---

### Post by slellis on 2010-03-30
Ok, guys,

I have solved the problem and would like to share the solution.

On the desktop:
Menu System > Administration > Users and Groups
The "Users Settings" window is opened.
Click on the "keys" button (Click to make changes)
Give the password -> Authenticate
Click on "Manage Groups" button
On the next window, select the group "lp"  and click on "Add user" button

From now on, you are added to the group of printers and everything will be ok.

Cheers,

Lellis

---

### Post by monicamaria on 2010-04-09
It finally works, thanks for all the help.  Here are the steps that worked for me:

On the desktop:
Menu System > Administration > Users and Groups
Click the keys to make changes, type password
Highlight you, the user, then click Properties
Under the "User Privileges" tab, scroll down and check the "Use Virtual Box" 
Click OK, then close.

Hope this helps.

Monica

---

