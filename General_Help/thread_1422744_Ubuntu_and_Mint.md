---
title: "Ubuntu and Mint"
date: 2010-03-05
forum: General Help
---

### Post by 3948ctyj on 2010-03-05
I am looking for a way to get some mobile broadband running on Linux. Ubuntu
has some networking stuff to help but it just doesnt work.... Ubun tu just doesnt recognize 
my EVDO usb modem.  I heard from a guy who says Mint worked right away...
What is mint and how is it different from Ubuntu.???
Why would Mint do a mobile broadband modem better than Ubuntu..??

---

### Post by Intrepid Ibex on 2010-03-05
> Linux Mint is an operating system for personal computers, based on (and compatible with) Ubuntu, with integrated media codecs. Mint also has design differences from Ubuntu, including:
[LIST]
[*]A distinct user interface, including the custom Mint menu.
[*]The Mint Tools, a collection of system tools designed to make system management and administration easier for end users.
[*]As of Linux Mint 6 'Felicia', a Windows installer is included as one of the installation methods, called mint4win, a rebranded version of Wubi. It is activated when the CD is inserted into a computer under Windows, providing AutoRun is enabled. However, in Linux Mint 8 'Helena' this feature was no longer available, due to incompatibility with GRUB 2, which was first used in that release
[/LIST]
([http://en.wikipedia.org/wiki/Linux_Mint](http://en.wikipedia.org/wiki/Linux_Mint))

It does seem quite attractive:

[img]http://upload.wikimedia.org/wikipedia/commons/b/b8/Linux-Mint-Helena.png[/img]

---

### Post by dcstar on 2010-03-05
> **3948ctyj said:**
> I am looking for a way to get some mobile broadband running on Linux. Ubuntu
has some networking stuff to help but it just doesnt work.... Ubun tu just doesnt recognize 
my EVDO usb modem.  I heard from a guy who says Mint worked right away...
What is mint and how is it different from Ubuntu.???
Why would Mint do a mobile broadband modem better than Ubuntu..??

Having just looked at it for the first time a few days ago, Mint just seems like a version of Ubuntu with the menus and apps reformatted to look more like a Windows system.

It probably makes the step from Windows to Linux easier for those who have been brainwashed.... I mean acclimatised... over the years to the Windows way of doing things.

I doubt it would do anything with hardware different than Ubuntu, but you can try it for yourself with a Live CD.

---

### Post by ron999 on 2010-03-05
@ 3948ctyj

Download **Linux Mint 8 "Helena" - Main Edition** and make yourself a live CD.
From here:-[http://www.linuxmint.com/edition.php?id=44]("http://www.linuxmint.com/edition.php?id=44")

---

### Post by tacantara on 2010-03-05
Linux Mint is based on Ubuntu, but it's packaging is somewhat different.  You can read more on Mint at [http://en.wikipedia.org/wiki/Linux_Mint](http://en.wikipedia.org/wiki/Linux_Mint).  I've tried it out, and it is a pretty good OS.  If that works better for you in setting up your EVDO USB dongle, then go for it.

---

### Post by lyall on 2010-03-05
see the following link for EVDO cards
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#EVDO_Cards]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#EVDO_Cards")

read the info for Sprint guide and/or Verizon guide

good luck and have fun learning

---

### Post by woodmaster on 2010-03-05
Ubuntu 9.10 here.  My verizon mobile broadband modem was auto recognized and all I had to do to connect was tell it it was Verizon.  Not sure what your carrier is but...Try going to System tab, Administration, Network Tools GUI and set up a new mobile broadband connection...

---

### Post by 3948ctyj on 2010-03-06
so you put it in the usb slot and it popped up and asked you the carrier..???
If so then 9.10 must have usb mode switch installed by default.  I am on 9,04
and I finally got my Novatel 760 flashing green and my system tried to connect but wouldnt.Verizon. I noticed you have to plug in the usb modem several times to get it to start up.
I put mode switch in from synaptic. I am wondering if Mint would do the trick..its based on 9.10 I think. There are some authentications that are editable in the mobile broadband form but I really would like Linux to do it for me.Its complex it seems.

---

### Post by noelvh on 2010-03-07
I have used both the USB, and PCMIA card form Verizon under both Ubuntu 9.04, and 9.10 with out any issue. All I had to do was plug them in and left click the network icon, and click on the broad band link in the menu. 
I was shocked at how simple it was. I know some cariers require user name and passowrd but Verizon did not.

Noel.

---

### Post by 3948ctyj on 2010-03-07
that sounds like great luck...I dont have that kind of luck with this stuff.

---

### Post by mosshorn on 2010-03-07
I had Linux Mint for a while, it's a good OS, had some issues with my laptop so I had to get rid of it. The custom menu is really well done, and while their package manager is OK, it's just that. OK. If your dongle works with it, I say it would be a great OS to use.

---

### Post by 3948ctyj on 2010-03-07
Now I have a little luck. I got my Verizon connection going. Here is some stuff for future Verizon folks and Novatel 760 USB modem folks.
First  is you have to use Windows to activate your USB modem. NO way around it.
Go to a Verizon store if you have to.
9.04 and 9.10 and Mint will work.REMEMBER the usb port must be on...if you dont have a green light its not on. Machines have so many these days.Move to one thats on.
Go into networks and edit connections and make a Mobile broadband connection.
Its already for you. It will do ALL the stuff for you. If you try to put in extra stuff like names and passwords then it might FAIL.Mine did until I got rid of that extra stuff.
Just select Country and carrier. PERIOD. Nothing else.
Save . You can reboot but you dont have to. Left clik on the network icon and you will see your new connection called Verizon and /or Auto Broadband connection. Check the box.
Within 10 seconds you will have a connection if you are near enough a tower. 
You will see a NEW icon on the bottom bar that looks like a mini tower. Its cute.
It doesnt have signal meter but who cares. AT least you know you are connected.
Praise God you dont have to use Windows,pathetic Windows.

---

