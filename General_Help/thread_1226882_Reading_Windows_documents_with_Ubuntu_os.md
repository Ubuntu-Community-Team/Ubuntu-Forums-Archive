---
title: "Reading Windows documents with Ubuntu os?"
date: 2009-07-30
forum: General Help
---

### Post by Camilia on 2009-07-30
I have a document, which is on a CD, that was written for windows os. I am unable to read it with Ubuntu os, which is the only os that I have on my pc.  I get many folders and sub folders.

Is there a program I can download to read the document on the CD?

---

### Post by rannable on 2009-07-30
It depends on the item you want to read, most likely is the item you want to open is created for a program you happened to have in Windows. Can you tell what file extention it is? Is it a MS Word document (.doc) or an Adobe .pdf file? Ubuntu has a bunch of programs and tools you can install to view just about anything...

As a quick answer I would suggest installing VLC media player for your audio/video needs and if you are running the latest version of Ubuntu it will come with OpenOffice which will open most MS Office documents and I believe Ubuntu comes with a PDF reader too...

---

### Post by Camilia on 2009-07-30
When I load the CD I see a on the desktop a CD WTLIBO7E. I click on it and get these folders:
rs_data
autorun.inf
extraDACfont.mcf
Readme.text
Systeminfo.exe
autorun.exe
EnabelAccesibility.reg
extraTTFfron.mcf
Setup.exe

I am at loss as to what to do. I tried clicking on fold and get more folders.

Don't see a media player.

---

### Post by NE Key on 2009-07-30
What you have there is not a document which can be passively read.
 
You have some kind of program to be run under winows. Do you have any idea what it does ?

A solution. Install Wine, this lets your Ubuntu box run programs written for windows.

---

### Post by kixome on 2009-07-30
If wine doesnt work, install virtualbox and run windows virtually. It is very easy and straight forward.

---

### Post by Camilia on 2009-07-30
> **kixome said:**
> If wine doesnt work, install virtual box and run windows virtually. It is very easy and straight forward.

Where do I find these programs?  Do I to reinstall ubuntu after I do this?  Particularly interested in the virtual box

---

### Post by prshah on 2009-07-30
> **Camilia said:**
> When I load the CD I see a on the desktop a CD WTLIBO7E. 
Don't see a media player.

This is not a media CD. It is the CD for WatchTower library 2007 edition. This is a Windows program, you need to install it. It is [rated platinum for wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10133"). The link also gives instructions, but in summary, just doubleclick setup.exe to start the installation.

---

### Post by pmlxuser on 2009-07-30
You install virtual box in ubuntu, go to application add/remove search virtual box.
and you don't need to reinstall ubuntu. virtual box is just like a program that runs in ubuntu allowing you to run other operating systems.

---

### Post by rannable on 2009-07-30
Hey Camelia, i would install virtualbox with Windows as a guest OS to run that, or risk WINE running it...

---

### Post by Camilia on 2009-09-17
I downloaded all the wine programs and still get boxes and boxes.  Went to link for platinum for wine. It says to remove old wine.  I guess I need to that but don't understand the instructions to do that.  Can't find virtual box. I am completely stumped.

---

### Post by XCan on 2009-09-17
To install Wine you should really use their repository for simplicity. If you follow the instructions at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) it should automatically take care of your old Wine version as well.

For virtualbox open Applications -> Add/Remove Applications and search for Virtualbox (make sure you select Show: All available applications).

---

### Post by Camilia on 2009-09-17
> **XCan said:**
> To install Wine you should really use their repository for simplicity. If you follow the instructions at [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) it should automatically take care of your old Wine version as well.

For virtualbox open Applications -> Add/Remove Applications and search for Virtualbox (make sure you select Show: All available applications).

Followed  the instructions, yet nothing has changed.  Didn't find virtualbox in add remove but found it in synapse manager. Still nothing has changes. Still have a bunch of boxes and boxes.

rs_data, autorun.exe, autorun.inf, EnableAccessibil, extraDACfont.mcf, extraTTFfont.mcf, Readme.txt, Setup.exe, Systeminfo.exe.

I clicked autorun.exe and got agreement. Still not getting anything usable.

I am at loss as to what to do.  For at the worst I can set up a dual boot up but they get very slow and irritating.

---

### Post by Camilia on 2009-10-09
> **XCan said:**
> 
For virtualbox open Applications -> Add/Remove Applications and search for Virtualbox (make sure you select Show: All available applications).

Finally Virtualbox available. I now have VBox Gtk and virtual box ose in accessories.  I followed the instruction for virtual box ose. Then inserted the Cd. The result was got message 

no bootable media found. System halted.

What can I do? Don't want to use wine, for I don't trust xp software since I read it had gotten corrupted and money stolen from bank accounts.

---

### Post by Camilia on 2009-10-24
> **rannable said:**
> Hey Camelia, i would install virtualbox with Windows as a guest OS to run that, or risk WINE running it...

You suggested I install virtualbox with Windows as a guest OS or risk using wine.

Been trying to the virtual box. Found I have to have a windows CD to do that. Only have the restore CD

Thinking of using wine but you stated it is a risk. Why did you say that?

---

