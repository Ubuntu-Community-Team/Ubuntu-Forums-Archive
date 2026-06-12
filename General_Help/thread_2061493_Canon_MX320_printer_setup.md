---
title: "Canon MX320 printer setup"
date: 2012-09-22
forum: General Help
---

### Post by Claypool on 2012-09-22
I am a new user using a dedicated desktop with 12.04 installed. My printer is a Canon MX320 multifunction. There is no Linux software from Canon available for this. There is a switch attached to the printer and connected to a laptop and my WIN7 desktop which I would like to retire and just use my other desktop with Ubuntu installed. I invoked localhost:631 to get to CUPS to add new printer but my model was not shown. Anyone with some suggestion? Help would be appreciated. Thank you.

---

### Post by TheFu on 2012-09-22
Options:
* Buy a new printer with Linux support.
* Locate commercial drivers for your Canon printer.

My mother had a Canon a few years ago. It made fantastic printed pages, though the ink was fairly expensive.  I found a commercial Linux driver for it for $50 - a 30 day trial was available.  It worked more like a Windows printer ... always had to run their driver software - ARRRRRGGGGGG!  When the 30 days was up, I gave that printer away and bought a Brother Laser print with support in Linux for $55.  That was 3 yrs ago. She's using the same toner cartridge today.

Myself, I have a cheap Samsung laser printer - also $55. It is supported with every distro that I've tried.  My Brother All-in-One inkjet is partially supported. I can fax and scan with it, but since the ink dried up 4.5 yrs ago, I've never replaced the ink.

Support for external devices will always be an issue for Linux and OSX and other less popular operating systems. The best advice is to carefully check that the device you are interested in owning is well supported by Linux and many different distros.  There are many HCLs (Hardware Compatibility Lists)  on the internet - there is one specifically for Linux Printing.

---

### Post by Claypool on 2012-09-22
Thanks for the advice. This is a challenge that I would like to conquer. My wife uses the mx320 also. It's only two years old anyway. I found a link: http:


[http://support-th.canon-asia.com/P/s...os&ca_os=Linux](http://support-th.canon-asia.com/P/s...os&ca_os=Linux)

I downloaded the file but am having a problem putting the command in terminal. Says it can't find the directory or file.

---

### Post by TheFu on 2012-09-22
What **exactly** did you type?

---

### Post by Pieman15 on 2012-09-22
I'm not sure if this will work, it's from the European Canon site, but there are Linux drivers. Might be worth a try:
[http://software.canon-europe.com/products/0010697.asp](http://software.canon-europe.com/products/0010697.asp)

---

### Post by Pieman15 on 2012-09-22
Whatever directory it says it can't find, you probably need to create before installing. 

sudo mkdir *directoryname*

---

### Post by Claypool on 2012-09-22
I typed this:

sudo dpkg -i --force-architecture ./cnijfilter-common_3.10-1_i386.deb

If I make a new directory, how do I copy that file into it?

---

### Post by TheFu on 2012-09-22
[http://ubuntuforums.org/showthread.php?t=1313992&page=2](http://ubuntuforums.org/showthread.php?t=1313992&page=2) - the very last comment seemed to have worked for them.

---

### Post by Pieman15 on 2012-09-22
I don't think you'll have to. You should be able to unpackage the .deb file from any location and it will place the files in the preassigned directory.

For your reference it would be sudo cp */fromdirectory /destinationdirectory*

---

### Post by pdc on 2012-09-22
crikey; 

it should just be a simple matter of installing the .deb package ..

**MX320series IJ Printer Driver Ver. 3.10 for Linux** (debian Packagearchive)

.......as one clicks from the Canon Asia site to download......

.......gdebi installer should leap to your rescue; and offer to install

why not start again.......go here..............

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100187502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100187502.html)

click to download the package that Canon make available for the MX320

.......gdebi should offer to install..........

then check here

[http://localhost:631/printers/](http://localhost:631/printers/)

(copy and paste into a spare browser window.....)

to see it is installed............

---

### Post by pdc on 2012-09-22
I guess it is interesting how often folks say things like

> There is no Linux software from Canon available for thi

and 

> 
Options:
* Buy a new printer with Linux support.
* Locate commercial drivers for your Canon printer.

.........coz I don't think the facts substantiate these views..

if one goes to the Canon Asia site, 

[http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal)

they have drivers for linux; either as source file, or rpm or deb ...

if you alternately go to Canon Europe

[http://software.canon-europe.com/](http://software.canon-europe.com/)

and indeed; *best of the lot*;

**Canon USA**

[http://www.usa.canon.com/cusa/support](http://www.usa.canon.com/cusa/support)

..........for all new printers, there seem to linux packages;

We had an ip5000; and are now using MG3160 and an LBP3150 and they work well.

---

### Post by Claypool on 2012-09-22
Thank you PDC I will try your suggestion.

---

### Post by pdc on 2012-09-23
If gdebi DOES NOT jump and offer to install:

if you use the GUI (clicking on icons method).......

you need to open your Downloads directory (where the cnijfilter-MX320etc should be......)

if you RIGHT-CLICK on the package, 

and select .....open with archive manager .....

.....then right-click on the cnijfilter-MX.. and select extract.......and extract to your desktop..

.....the command is OPEN at the bottom right, the way you open any file..

.......*then you get what I show in the extract_file screenshot*

then click on "SHOW THE FILES"

and you can see the cnijfilter-MX package........

.....double-click to open it; 

and you will see an install.sh script...........

RIGHT-CLICK on that.

*and you will see the install_sh screenshot*

select RUN IN TERMINAL

[I]that gives you the final screenshot, the terminal screenshot:
[/I]
you can see it is set up with the gdebi installer command; all ready to go; when you enter your sudo password; 

this all may seem complicated; but I hope the instructions are clear;

and you may value working through the steps only; later;

just to see the way installing and packages are managed

---

### Post by Claypool on 2012-09-23
OK I finally got to extract that file in the terminal. When I opened localhost:631/printers nothing showed so I opened localhost:631/  add a printer/selected canon/ found the mx320 and clicked on it. It appeared to install and went through a basic setup. Tried to print a test page and nothing happened. Opened a Libre document to test print but nothing happened. Did I do something wrong? In the initial printer setup, only option was to select LPT1 but it is connected via USB, maybe that's the problem?

---

### Post by Claypool on 2012-09-23
OK I finally got this to work. The problem was with the IO Gear printer switch between the laptop and my WIN 7 unit. When I attached the Linux unit directly to the Canon, I was able to print and also do a scan. Now, all I would need is a USB cable with a true Y end so I could plug the laptop and the Linux unit together into it. Anyone know of such a cable I could get?

---

### Post by pdc on 2012-09-23
............entered not realising poster had got his cables mixed up

---

### Post by Claypool on 2012-09-23
pdc, I have it already installed. I am not following you on your last posting. I also installed the scanner driver as well and both are working. As I mentioned, the issue was with the IO Gear printer switch and when I attached the computer directly to the printer that was the answer. I was able to go through the install in terminal I thank you for you great help. Much appreciated. Do you know where I can get a USB cable with a true Y double male end by any chance?

---

### Post by pdc on 2012-09-23
[http://lmgtfy.com/?q=IO+Gear+printer+switch+USB+cable+with+a+Y+double+male+end](http://lmgtfy.com/?q=IO+Gear+printer+switch+USB+cable+with+a+Y+double+male+end) :p :p

---

### Post by Claypool on 2012-09-23
Thanks for the Google search. I will check it out and see if I can find anything that may work for me.

---

