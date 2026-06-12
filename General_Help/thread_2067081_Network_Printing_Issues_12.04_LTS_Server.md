---
title: "Network Printing Issues 12.04 LTS Server"
date: 2012-10-06
forum: General Help
---

### Post by Lorek on 2012-10-06
I'm running 12.04 LTS Server and I'm having several issues with printing. 
Initial setup went by like a breeze, CUPS is all set up and listening to the right ports the printer driver appears to be installed correctly (Canon MP160 USB) and when printing from a Windows 7 Client it detects printer and does print. After that is where the problems start, for example I'll print using a browser on my windows client. The printed page comes out with three problems;  black and white, formatting messed up, and randomly stops for long periods of time halfway through a page (~15-20 mins). I thought maybe the printer driver wasn't correct so I found an article indicating adding a PPA repository and using sudo apt-get install cnijfilter-mp160series unfortunately that's not currently available (something to do with the repository pckmgr) so I'm stuck. Any ideas on how I can get this running properly?

---

### Post by albandy on 2012-10-06
Create a new printer with the same connection and put it in raw mode. Then configure this printer in windows clients and select the original printer driver.

This worked for me with a cheap laser printer.

---

### Post by pdc on 2012-10-06
so I'm not clear which printer driver you are using for your MP160; or where you got it from;

as an ubuntu user, a debian package would be good; 

........looking at the Canon Asia website..they provide linux drivers..but only in the rpm format

however alien should convert them

with Canon, one needs to install what they call the common package first; and then the specific driver..

so go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900718411.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900718411.html)

for the [COLOR="Red"]IJ Printer Driver Ver. 2.70 for Linux (rpm Common package)
[/COLOR]

....it comes in as [COLOR="SeaGreen"]cnijfilter-common-2.70-1.i386.rpm[/COLOR]

and go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900705501.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900705501.html)

for the [COLOR="Red"]IJ Printer Driver Ver. 2.70 for Linux (rpm Package for MP160)[/COLOR]

.....it comes in as [COLOR="SeaGreen"]cnijfilter-mp160-2.70-1.i386.rpm[/COLOR]

to install alien use synaptic or 

> sudo apt-get install alien 

and the install command using it should be

> sudo alien -i *package*.rpm

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

__________________________________________________

Canon make scangear available to drive the scanner if you need it..

---

### Post by Lorek on 2012-11-04
Thanks pdc, I was using the default driver that installs when I installed CUPS which was Canon PIXMA MP160 - CUPS+Gutenprint v5.2.8-pre1(en). I didn't see those packages at canon.com so thanks for the links. 

I installed those as you suggested with alien and that seems to have fixed my formatting problems with text. I am still having issues printing color as all printed pages only come out in black and white. For example when printing this forum page, the orange banner "ubuntu forums logo" at the top is invisible for everything except for text like "Search" and "Board Listing > Post". So the orange banners are not showing up nor are the table borders. 

I must admit I don't have much experience with the shell prompt beyond basic system commands and pipes and a limited understanding of configuration files gleaned from reading numerous ubuntu articles.
That's slowly changing since I'm working with the server edition now and can't rely on gui but its slow going, thanks for your help.

Update: Currently the settings for my CUPS server are set to RGB Color (definitely not grayscale) but there are several more advanced settings which I'm unsure of. Output Control Common, Color Correction is set default, 1.0 for all settings (excl adjustment), Brightness Contrast Saturation = 1.000. All color settings under Output Control Extra 1/2/5 are set to 0.000 by default. Also even though I installed the canon drivers they don't appear to be showing up under the driver list on modify drivers even after a CUPS restart. After restarting the server there did appear a new local device but CUPS threw a bunch of errors when trying to modify it via web interface. Under Local Devices: USB Printer #1 with status readback for Canon IJ  showed up with connection: cnij_usb:/dev/usb/lp0, and attempting to modify it yields a Bad device-uri "cnij_usb:/dev/usb/lp0".

Update2: I Should also mention I'm using CUPS v1.5.3

---

### Post by pdc on 2012-11-04
glad things are moving along for you;

colour issues.......... when I look in my CUPS settings for my MG3160, I see

> Driver:	Canon MG3100 series Ver.3.60 (color, 2-sided printing)

and I guess that was set from the Menu: Printing options ..also accessed by system-config-printer

......I see some of these messages about not printing colour and am not sure about them:

to edit OpenOffice I use the command

> [COLOR="Red"]/usr/lib/libreoffice/program/spadmin[/COLOR]

and one can tinker in there too

---

### Post by Lorek on 2012-11-04
Yeah I'm a bit stumped at the moment, I'll probably dive into the CUPS/printer configuration and documentation when I have some time in a week or two. I usually use nano / vi for text editing. Its a headless server so I do most of the configuration changes through a SSH shell. I've included a couple links to snapshots I took of what options I have available from CUPS Web interface for clarification in case someone sees an easy fix.

[Screenshot 1]
[IMG]http://i50.tinypic.com/2lub9c0.jpg[/IMG]
[Click to Enlarge]("http://i46.tinypic.com/foos2u.jpg")

[Screenshot 2]
[IMG]http://i50.tinypic.com/xbwc91.jpg[/IMG]
[Click to Enlarge]("http://i47.tinypic.com/2110304.jpg")

[Screenshot 3]
[IMG]http://i46.tinypic.com/n5272f.jpg[/IMG]
[Click to Enlarge]("http://i50.tinypic.com/2rokkcp.jpg")

---

### Post by pdc on 2012-11-04
> *[COLOR="Magenta"]I installed those as you suggested with alien[/COLOR]* and that seems to have fixed my formatting problems with text.

....... I can't see the Canon driver listed .......

what does 

> [COLOR="Red"]sudo dpkg -l | grep cnijfilter*[/COLOR]

show?

---

### Post by Lorek on 2012-11-05
The command sudo dpkg -l | grep cnijfilter* 
has no listing matches.

echo
> lorek@yggdrasil:~$ sudo dpkg -l | grep cnijfilter*
lorek@yggdrasil:~$ [] where [] represents cursor.

However after manually looking through the listing with 
sudo dpkg -l | more I found the listing.

> lorek@yggdrasil:~$ sudo dpkg -l | grep "cnijfilter*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/           Name                     Version                  Description
+++-========================-========================-================================================================
ii  cnijfilter-common        2.70-2                   IJ Printer Driver Ver.2.70 for Linux
ii  cnijfilter-mp160         2.70-2                   IJ Printer Driver Ver.2.70 for Linux
ii  grep                     2.10-1                   GNU grep, egrep and fgrep
lorek@yggdrasil:~$ []

Although the forum posts don't really preserve the table formatting [3 columns, Name, Version, Description]

---

### Post by Lorek on 2012-11-05
> **airynmanj said:**
> Then configure this printer in windows clients and select the original printer driver.

That's already been done, the client is properly setup the problem is originating from the server hosting the printer.

---

