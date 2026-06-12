---
title: "XSane Scanning does not pick up Printer Epson Stylus TX100"
date: 2009-08-31
forum: General Help
---

### Post by daaussie on 2009-08-31
XSane Scanning does not pick up Printer Epson Stylus TX100

The printer works fine and prints in colour, even off the network.

BUT I click XSane and says no device is connected.

What the???

---

### Post by daaussie on 2009-08-31
anyone?? just trying to move this..

---

### Post by ZWM on 2010-03-03
I'm having the same problem, but I only want to use the scanner. The drivers and all software on it's CD don't work in Wine. Same peripheral on same PC worked fine under XP SP3, but won't work under Ubuntu 9.1. Other peripherals (like USB drives) are found and put on the screen automatically with no input from me so I know it's not my USB slot. Tried swapping over the USB cable, same result. Open Office finds it as a Printer, but I actually don't want to use it as a printer. Xsane, Image Scan!, the Felugia one, and even SANE itself won't find this peripheral *as a scanner*, and I'm going to try any others that I find. The TX100 is listed on SANE site as having GOOD native support, so these problems that many users face strike me as being odd.

---

### Post by daaussie on 2010-03-03
sorry to hear you have the same problem. Hoping you find a solution for the both of us. The printer component of this is very expensive. I bought a cheap (1/3 of the price) HP deskjet all in one, and it worked fine for both printing & scan....

Wish that Epson would get its act together & help us use their LATEST printer!

---

### Post by ellgor on 2010-03-04
Hi,

Go to the "Avasys" site and look for the Imagescan app for your model, get the deb package as its easier to install, needs areboot to start.

Rergards, Ellgor.

---

### Post by daaussie on 2010-03-27
tried this avasys site, and the scanner software is still not allowing scan function.

I am pretty disappointed with Epson Stylus TX100 because this cost me double compared with my "working" HP Deskjet F370 scanner. 

I should have got another HP, it was half the price and scanned fine with no problems!

(I have a need for 2 scanners in our office).

---

### Post by ellgor on 2010-03-28
Hi,

Sounds like a permission issue, check to see if you have put yourself into the, lp and sane group, "System-Admin-User's" then try starting Imagescan from a terminal :

sudo imagescan

hopefully that will get it running.

Regards, Ellgor.

---

### Post by daaussie on 2010-03-29
Hey Ell,

I am not sure how to check permissions. Do you do this from Terminal? What are the commands?

Cheers
A,

---

### Post by ellgor on 2010-03-30
Hi,

Just run the command, in a terminal, as shown above :

sudo imagescan   (or even "sudo xsane" (no quotes) if you have xsane)

that should run it.

Regards, Ellgor.

---

