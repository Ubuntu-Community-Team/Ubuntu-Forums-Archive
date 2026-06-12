---
title: "how to play wifi install cd"
date: 2011-05-24
forum: General Help
---

### Post by jesse c on 2011-05-24
I have 11.04 installed and was having wifi dropout from my usb wifi dongle so i thought id get a new one so i picked up an Asus usb that claims to be Linux capable but i dont know how to play the install disk that came with it.I dont know how to do the 'extract' thing i guess.Im used to Windows where you just push a disk in and it just plays.Maybe there is an application i should install first .Looking for step by step tutorial

---

### Post by nitstorm on 2011-05-24
Little more information would be nice.

Open a terminal and type in the following

```

ls -la /path-of-the-cd-location-goes here

Example : ls -la /media/MyCD

```


These links might also help:[URL="http://www.tuxfiles.org/linuxhelp/softinstall.html"]
http://www.tuxfiles.org/linuxhelp/softinstall.html[/URL]

---

### Post by jesse c on 2011-05-24
youre over my head already with the 'path' thing.I know how to put a disc in the slot and thats about it.

---

### Post by Mark Phelps on 2011-05-24
> **jesse c said:**
> I have 11.04 installed and was having wifi dropout from my usb wifi dongle so i thought id get a new one so i picked up an Asus usb that claims to be Linux capable but i dont know how to play the install disk that came with it.I dont know how to do the 'extract' thing i guess.Im used to Windows where you just push a disk in and it just plays.
You don't "play" a software disk; instead, what "autoplay" does in MS Windows is look for certain startup files on the disk and, if found, executes them -- which will do you no good in Ubuntu.
> Maybe there is an application i should install first 
NO -- there is not an application you install.
> .Looking for step by step tutorial
First thing you need to do is find out what files are actually on the disk.  Since you're familiar with Windows, suggest you stick the CD into a Windows machine, open up a file manager (Windows Explorer?) and write down the directories found on the CD.

What you're looking for is a directory that has files you need to either install a Linux driver or "make" a Linux driver from source.

Until we know what files are on the disk, no one can provide step-by-step instructions.

---

### Post by Ibidem on 2011-05-24
Linux compatible? I'd suggest seeing if it works already. Generally, Ubuntu has most of the drivers you'll use, and a whole ton more.

If it doesn't, there should be a CD icon on the desktop or in the left panel of Nautilus (assuming you use Ubuntu with Gnome).  Double-click on that, and it will open the CD.  I'd recommend looking at whatever README or HTML file they have; that's as far as I can point you without knowing what the CD has and which model you have.
Is it by chance the USB-N-10?

---

### Post by jesse c on 2011-05-24
Ok i hit a few buttons and came up with a 'readme' file that mentions being linux 2.4/2.6 kernel compatible and continues to go thru a massively complex driver install text
My usb is an Asus USB N 13  and uses a Ralink RT2870 linux driver according to 'readme' file

---

