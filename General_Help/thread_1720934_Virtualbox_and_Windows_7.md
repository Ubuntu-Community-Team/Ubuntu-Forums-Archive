---
title: "Virtualbox and Windows 7"
date: 2011-04-03
forum: General Help
---

### Post by Rikeshar on 2011-04-03
Hey guys, not sure where this should go, so I chose general. I've been trying for almost a week to get this working and have been unsuccessful. No one on the Virtualbox forums seems to know a solution.

The problem I'm having is that my Windows 7 guest will not start USB devices, which means I cannot use flash drivers, my iPhone, etc. It's really quite frustrating. I have version 4.0.4 OSE, Guest Additions and the Extention Pack are loaded. 

My host computer, Ubuntu, will recognize the devices, the Virtualbox program will recognize them, the Windows 7 guest will -recognize- them, but they all show errors, saying that the device cannot be started. If I try updating the drivers, it either fails or tells me I have the latest drivers.

See the attached screenshots for more:

---

### Post by wilee-nilee on 2011-04-03
You need the puel version not the OSE.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

You then open the users and groups go to vbox and tick yourself on, add the usb in the edit section of the machine and that is it.

You can use the machines you have now in the puel.

---

### Post by Rikeshar on 2011-04-03
I figured that might be the case. They don't have a package for 11.04 yet, and if I try the one for 10.10 the Software Center won't open it. Any suggestions with that?

---

### Post by wilee-nilee on 2011-04-03
> **Rikeshar said:**
> I figured that might be the case. They don't have a package for 11.04 yet, and if I try the one for 10.10 the Software Center won't open it. Any suggestions with that?

Download the linux hosts from my link it will run fine, it is Natty that will be your problem if any.

We have to assume guest additions and kernel allowance though at this point.

---

### Post by Rikeshar on 2011-04-03
Okay, yeah, just be because of Natty. When you go to the website they don't have an option for it yet, and when trying to install the .deb from Maverick I get:

```

thornbury@Zach-Ubuntu:~$ sudo dpkg -i virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb
dpkg: error processing virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb

```

---

### Post by wilee-nilee on 2011-04-03
> **Rikeshar said:**
> Okay, yeah, just be because of Natty. When you go to the website they don't have an option for it yet, and when trying to install the .deb from Maverick I get:

```

thornbury@Zach-Ubuntu:~$ sudo dpkg -i virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb
dpkg: error processing virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb

```

Just download the deb, then run in the terminal 
sudo apt-get install gdebi. Go to the downloaded deb right click and open it with gdebi.

This page all distributions at the bottom. I just noticed that this is downloading a bin file use the maverick version.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Rikeshar on 2011-04-03
Aha! That works! Thanks, and what a great tool to have regardless. I'll give it a try and see what happens.

**EDIT**

IT WORKS! WOO! Man, I should have just asked here first, I've been trying for literally a week now to get this working! Thank you so very much.

---

### Post by wilee-nilee on 2011-04-03
> **Rikeshar said:**
> Aha! That works! Thanks, and what a great tool to have regardless. I'll give it a try and see what happens.

**EDIT**

IT WORKS! WOO! Man, I should have just asked here first, I've been trying for literally a week now to get this working! Thank you so very much.

I would say overall this is one of the best forums, for all programs really it is just large enough for it to play out this way at times.:)

---

### Post by Rikeshar on 2011-04-03
I'd definitely agree with you there. Very helpful. Hopefully one day I'll be proficient enough to give back what's been given to me. Thanks again. :P

---

