---
title: "HP Photosmart D110A All in one wireless printer"
date: 2011-04-22
forum: General Help
---

### Post by asnd16 on 2011-04-22
I am trying to print to my HP Photosmart e-All-in-One CN731A wireless printer.  Is this possible? I am running Ubuntu 10.10 Netbook remix i belive .. . 

Also if anyone knows how to remove the side bar let me know . .

---

### Post by rocket321 on 2011-04-23
Ok I incurred the same problem and it is possible to get it online. Although I am using 10.10 desktop I hope I can point you in the right direction. My comp and printer were connected through usb during this.

I followed these steps and then did my own tinkering. 
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

I did the sudo hp-setup, but got some errors.
One of the errors was 
**error: hp-setup requires GUI support**

It says one might get this with 9.10, but I am running 10.10.
So I typed in the terminal  **sudo apt-get install python-qt4**, hoping to correct it. I then typed **sudo hp-setup** and it worked, but still with some errors.
Anyways, it pulled up the setup process and I couldn't get the printer up wirelessly because no devices were discovered. So I closed it out. I then went to
System->Administration->Printing

I clicked the add button, a window pops up. Hit network printer and choose appsocket/hp jetdirect, typed my printers ip address for the host. It pulled up another window with 2 out of the 3 boxes filled with my printers name/model and I left the last box empty. Hit forward/enter. It asked if I wanted to print a test and hit ok. It printed, but I was still wired and took out the usb, crossed my fingers, and did another test print wirelessly and it worked!!!!!!


Astoria, huh? My friend lives there. Fun place to go out.

---

### Post by asnd16 on 2011-04-24
> **rocket321 said:**
> Ok I incurred the same problem and it is possible to get it online. Although I am using 10.10 desktop I hope I can point you in the right direction. My comp and printer were connected through usb during this.

I followed these steps and then did my own tinkering. 
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

I did the sudo hp-setup, but got some errors.
One of the errors was 
**error: hp-setup requires GUI support**

It says one might get this with 9.10, but I am running 10.10.
So I typed in the terminal  **sudo apt-get install python-qt4**, hoping to correct it. I then typed **sudo hp-setup** and it worked, but still with some errors.
Anyways, it pulled up the setup process and I couldn't get the printer up wirelessly because no devices were discovered. So I closed it out. I then went to
System->Administration->Printing

I clicked the add button, a window pops up. Hit network printer and choose appsocket/hp jetdirect, typed my printers ip address for the host. It pulled up another window with 2 out of the 3 boxes filled with my printers name/model and I left the last box empty. Hit forward/enter. It asked if I wanted to print a test and hit ok. It printed, but I was still wired and took out the usb, crossed my fingers, and did another test print wirelessly and it worked!!!!!!


Astoria, huh? My friend lives there. Fun place to go out.



Yeah there are loads of things to do around here.  Cool, same here on installing the sudo apt-get install python-qt4 first.  After that is seems it would work.  I got to get a usb cord from work tomarrow to finalize the project. Thanks for the info. :D

---

### Post by rocket321 on 2011-04-25
Oh, I forgot to mention you will have to choose the printer for wireless printing. If you're printing from open office, go to file then printer settings toward the bottom. A window will pop up showing the name of the default printer. If you  have been able to get the printer up wirelessly it will show two names for the one printer. My wireless printer's name is HP-Photosmart-d110 and the wired name is Photosmart-D110-Series.

---

### Post by asnd16 on 2011-05-05
Here is my error when I sudo hp-setup 


Searching on USB bus...
error: No devices found on bus: usb

---

