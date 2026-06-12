---
title: "network adapter driver"
date: 2010-10-20
forum: General Help
---

### Post by Grey Seal on 2010-10-20
**F5D7050 connectivity** 			 			 			 		   		 		 		Dell GX, Kubuntu 10.04, K 2.6.32, FF 3.6.1, Clear modem, Netgear Wi-Fi router

Just received network adapter and unable to install 
Belkin service was useless
Unable to find an answer in the forum
Moved computer, running point to point on the LAN
Searching for a compatible driver and/or means of installation
Poor connection with Clear and modem's on top floor, Belkin's a good option 

Need some help to install it

Thanks
GS

---

### Post by chessnerd on 2010-10-20
If Ubuntu isn't recognizing the card, you could try using the Windows XP driver via NDISWrapper.
[http://www.belkin.com/support/ab/c/](http://www.belkin.com/support/ab/c/) - will give you the XP driver

```
sudo apt-get install ndisgtk
```

ndisgtk will give you the graphical front-end and, since it depends on them, the back-end packages. 

From there, just follow these steps:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Grey Seal on 2010-10-20
Thanks.
I read through several sites and it appears that the first step is
- sudo apt-get install ndisgtk - installing the wrapper
Next downloading the XP driver which the wrapper would install, but do not know how the file executes
Will that work?
WifiDocs/Driver/Ndiswrapper was confusing since my OS is 10.04

Appreciate the response
GS

---

### Post by chessnerd on 2010-10-20
NDISWrapper uses inf files, but it looks like the website is giving you an executable.

You wouldn't happen to have a Windows machine that you could install it on, do you? If you do, install it and then go grab the inf file from the drivers folder (probably C:\system32\drivers or something like that). Otherwise, you could search online for the inf file.

---

### Post by Grey Seal on 2010-10-20
[I]NDISWrapper uses inf files, but it looks like the website is giving you an executable.

You wouldn't happen to have a Windows machine that you could install it  on, do you? If you do, install it and then go grab the inf file from the  drivers folder (probably C:\system32\drivers or something like that).  Otherwise, you could search online for the inf file.[/I] 

Thanks, I have an XP laptop right here but never used anything other than DOS based OS before Linux. I have the site address from which to download the driver but not sure where to put it in order to use it for Kubuntu. Then where to put it in here and how to access it. The adapter is a few years old (B), just figured the plug-in would be recognized.

Again thanks for the assistance

---

