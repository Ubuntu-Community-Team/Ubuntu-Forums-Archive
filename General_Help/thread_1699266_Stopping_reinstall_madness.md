---
title: "Stopping reinstall madness?"
date: 2011-03-03
forum: General Help
---

### Post by pluMmet on 2011-03-03
From time to time I reinstall Ubuntu for whatever reason. I have to go thru all the steps of installing all the stuff I use but then I have to search down all these little additional things I need to make the programs work. Amarok for instance does not work until I do a search to find out these 2 files that I have to install thru the terminal. The problem is that there are allot of these little files that I have to search down and install and just the searching for what file it is gets tiring over and over.

I'm sure I can keep a text file with every little thing I do and try to keep it updated but I'm hoping that it's easier then that. Can I save the current state of Ubuntu as an image that will just deploy fully enabled back onto my computer? Or is there some way to handle this that I haven't thought of?

---

### Post by Verbeck on 2011-03-03
you can use remastersys to make an installable live iso image file of the current system
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by pluMmet on 2011-03-03
Verbeck you're lightning quick :KS gold star for you :)

---

### Post by ezsit on 2011-03-03
look into remastersys.com. This tool allows you make a liveCD or DVD from your installed system as a full backup (limited to 4.3GB) or as a distributable system only backup without personal files and customizations yet containing all software added to the system.

---

### Post by indytim on 2011-03-03
If you're not jumping versions of Ubuntu (or any other Lx), one possibility is to image backup your ops partition (and /home if separate).  A partition level restore will bring the partition back to the state that it was in at the backup point.  There are lots of image backup apps available in Lx-land.  My favorite is fsarchiver.  Clonezilla is another popular option.

IndyTim / DataMan

---

### Post by howefield on 2011-03-03
Also, have a look at clonezilla.

This is a Live CD which will create an image of your partition(s)/disk(s).


clonezilla.org

---

