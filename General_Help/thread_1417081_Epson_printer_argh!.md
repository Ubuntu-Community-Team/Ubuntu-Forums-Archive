---
title: "Epson printer argh!"
date: 2010-02-26
forum: General Help
---

### Post by BrockStrongo on 2010-02-26
I've been trying to get my new Epson NX215 working for about three weeks now, and I'm ready to smash the thing. 
  I got the scanner working using Image Scan!, but cannot get it to print anything. All it does is spit out blank pages till it is out of paper. 
I have downloaded the driver and have both Gutenprint and Cups.
  I can get it to print when using the printer in my windows virtual machine, but would prefer to not have to start up vmware every time I want to print something.
   I'm pretty sure this is a driver or postscript issue as I have used other printers, even an epson, with this exact same machine.
  Any ideas?

---

### Post by llamabr on 2010-02-26
[http://ubuntuforums.org/showthread.php?t=1353566](http://ubuntuforums.org/showthread.php?t=1353566)

---

### Post by BrockStrongo on 2010-02-26
Worked like charm, thanks a lot for pointing me in the right direction.
one more question, should I use the generic eklite.ppd or the device specific ppd that was downloaded from avasys. I am sure I could just try them both but I am a lazy man.
THANKS SO MUCH FOR YOUR HELP, AND ALL THE HELP FROM THIS FORUM.

---

### Post by Mark Phelps on 2010-02-27
Given the ease with which you can change PPDs (just reconfigure using CUPS and select a different PPD file), I would suggest you try each one.

I have an Epson printer attached and tried several different PPDs until I settled on the latest one provided by CUPS as the one with the best set of features.

---

### Post by allain on 2010-08-23
I have had a similar problem with Epson NX215 and was able to resolve it by downloading the deb package from the website specified above Avasys(?) website.

---

