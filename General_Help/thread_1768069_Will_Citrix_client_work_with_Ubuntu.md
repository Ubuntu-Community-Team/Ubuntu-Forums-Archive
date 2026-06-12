---
title: "Will Citrix client work with Ubuntu?"
date: 2011-05-26
forum: General Help
---

### Post by Deaf Smith on 2011-05-26
According to our hospital they have Citrix severs set up and we can set it up for home use (logon our severs that is.)
 
According to them Operating Systems inculude Red Hat Linux and Mozillla Firefox 1.0.4.
 
So, what about Ubuntu? 
 
Shall I try it tonight?
 
Thanks!

---

### Post by jerryjustly on 2011-05-26
Mozilla FireFox is a web browser and Ubuntu comes with it as default.  One way to try Ubuntu is to download the Ubuntu iso image and burn it to a CD.  You can then insert the CD into your computer and boot up.  After a period of time, a window will popup asking if you want to try Ubuntu or install ubuntu.  Click the "Try Ubuntu" button.  The computer will then continue to boot using the CD as it would a hard drive and leaving your own hard drive completely alone.  When in Ubuntu try opening Firefox and seeing if you can access the stuff you want.

--------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages.

---

### Post by Deaf Smith on 2011-05-27
Jerry,
 
Thanks. I already have Ubuntu but what I don't know is if Citrix will work with it. I suspect the deb packaging is not compatable with the rpm style that Red Hat uses.
 
It didn't fly last night but I'll try a bit more tonight.

---

### Post by LordNeo on 2011-05-27
You could try to use "alien" to convert the rpm package.
Some time ago i used Citrix Xen Center to manage my remote Xen Servers, so i guess there must be a way to get it working

---

### Post by linuxinstalledfromhdd on 2011-05-27
Daily I use Citrix ICAClient with Ubuntu successfully. You need to be running a 32-bit version of Ubuntu, because the ICAClient intaller is a 32-bit Deb package installation, and plugin for Mozilla Firefox.  They can be --force installed, but you will not get the plugin for Firefox to install automatically. 

Here is more information:

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

---

### Post by Deaf Smith on 2011-06-03
Much thanks.
 
I will try it tonight.

---

### Post by Steeperton on 2011-06-03
> **linuxinstalledfromhdd said:**
> Daily I use Citrix ICAClient with Ubuntu successfully. You need to be running a 32-bit version of Ubuntu, because the ICAClient intaller is a 32-bit Deb package installation, and plugin for Mozilla Firefox.  They can be --force installed, but you will not get the plugin for Firefox to install automatically. 

Here is more information:

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

I'm using Citric Receiver with 64 bit Ubuntu (admittedly not with a firefox plugin - not sure what that's for... Just make sure ia32-libs is installed, and all's good.

---

