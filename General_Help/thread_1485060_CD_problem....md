---
title: "CD problem..."
date: 2010-05-16
forum: General Help
---

### Post by mclizardman24 on 2010-05-16
Hi.
I am trying to install the software for my wireless usb card, but when I put the disk in the drive the icon comes up. When I click on it has a bunch of different option, and one of them is setup. When I double click it, I get this message: 
 
Archive: /media/cdrom0/setup.exe
Zip file size: 4611104 bytes, number of entries: 29842
 
     [/media/cdrom0/setup.exe]:
     Zipfile is disk 39299 of a multi-disk archive, adn this is not the disk on
     which the central zipfile directory begins. Cdisk(3569)
 
Thanks for the help, and also, my other question, please: [http://ubuntuforums.org/showthread.php?t=1484382](http://ubuntuforums.org/showthread.php?t=1484382)
 
Thanks again!

---

### Post by Snow986 on 2010-05-16
This is a windows .exe file, it wont run in linux.  What is your wireless usb card model?  In linux, you might only need the driver, or it might be installed for you automatically.

---

### Post by mclizardman24 on 2010-05-16
> **Snow986 said:**
> This is a windows .exe file, it wont run in linux. What is your wireless usb card model? In linux, you might only need the driver, or it might be installed for you automatically.
 
The box says: Belkin N150. (Also, seeing on the side it says PC running Windows, because I originally bought this for a Windows Computer. Would it still work on Linux?) Also, I have a hard time connecting to the web, it dosen't seem to know that the card is in there...

---

### Post by Snow986 on 2010-05-16
Have a look here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You can also check to see if anyone has it working by googling a bit.  Typically you can try things like Ndiswrapper or ported drivers for linux.  

To see if the card is recognized try opening terminal and running 
```

lsusb

```

If the card shows up then your computer at least recognizes it.

---

### Post by mclizardman24 on 2010-05-16
> **Snow986 said:**
> Have a look here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
 
You can also check to see if anyone has it working by googling a bit. Typically you can try things like Ndiswrapper or ported drivers for linux. 
 
To see if the card is recognized try opening terminal and running 
```

lsusb

```
 
If the card shows up then your computer at least recognizes it.
 
It showed up on the third line i think. i do have a little symbol at the top of the screen that looks like a little wireless thing, but it is faded.

---

### Post by samg34 on 2010-05-16
try downloading a linux version of your driver or getting something that can read .exe like WINE
I had a similar issue  [http://ubuntuforums.org/showthread.php?p=9309760](http://ubuntuforums.org/showthread.php?p=9309760)

---

