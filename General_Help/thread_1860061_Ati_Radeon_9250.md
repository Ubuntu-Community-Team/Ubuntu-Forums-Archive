---
title: "Ati Radeon 9250"
date: 2011-10-14
forum: General Help
---

### Post by aki993 on 2011-10-14
Where can I find driver for Ati Radeon 9200/9250. I'm running Ubuntu 11.10

---

### Post by wanderingarticfox on 2011-10-14
Did you just upgrade from 11.04? If you had the ATI Catalyst Driver and Centre before it should have carried over. If you did a 'clean' install then use the Additional Drivers option.

---

### Post by collisionystm on 2011-10-14
> **aki993 said:**
> Where can I find driver for Ati Radeon 9200/9250. I'm running Ubuntu 11.10

Sudo apt-get install fglrx

---

### Post by aki993 on 2011-10-14
In aditional drivers it says there is no poprietary drivers in use on this system.
I'll try this with apt-get.

---

### Post by aki993 on 2011-10-14
It says fglrx is already the newest version.

---

### Post by collisionystm on 2011-10-14
Run the catalyst control center that should have installed.

---

### Post by wanderingarticfox on 2011-10-14
> **aki993 said:**
> It says fglrx is already the newest version.

I'm not in Unity now so I cannot walk you to it but click on the top item in the task bar [I think it is called]; what you are looking for is the Icon for the ATI Catalyst Control, should be two; use Admin. use your main password and you cans adjust some things in your resolution, color 3-d, etc.  This where you can activate the driver too.

---

### Post by crdlb on 2011-10-14
Fglrx does not support such and old video card. You should uninstall fglrx and use the builtin radeon driver.

---

### Post by Nytram on 2011-10-14
I think you're out of luck with the 9250, I've got the same card and been unable to get a driver working for it.

---

### Post by aki993 on 2011-10-14
p, li { white-space: pre-wrap; }  There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 
 No AMD graphics driver is installed, or the AMD driver is not functioning properly.
 Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.


Thats says when I open Catalyst Control Center

---

### Post by aki993 on 2011-10-14
Nytram we need to install first ubuntu release to get this card work :D

---

### Post by ragnarok1 on 2011-10-17
For those that have a card being read as an RV280, which includes these: Radeon 9200PRO/9200/9200SE/9250, and M9+, the ATI Driver works better for it. If you use the FGLRX driver, it will most likely list your Graphics as UNKNOWN in System Info. To fix this. Open this url and scroll down to "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch". Then, push Ctrl+Alt+T in order to open the Terminal. Enter all of the commands as given on the page, except for the one that is separate. Once you complete the, restart the computer and go to System Info. Your Graphics card should be properly detected if it is a member of the RV280 class, which includes these[FONT=monospace] [/FONT]Radeon 9200PRO/9200/9200SE/9250, and M9+.

---

### Post by Mark Phelps on 2011-10-18
AMD (formerly ATI) dropped fglrx driver support for your series card YEARS ago.  The drivers that work now are the default open-source drivers -- and these are installed automatically when Ubuntu is initially setup.  Trying to force the installation of fglrx drivers, or Catalyst Control Center, is only going to hose up your display -- forcing you to remove it and replace it with the default open-source drivers.

---

