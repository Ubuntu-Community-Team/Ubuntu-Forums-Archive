---
title: "Installed Ubuntu 11.04 and now problems with wireless connectivity"
date: 2011-06-05
forum: General Help
---

### Post by suomik1988 on 2011-06-05
I have an older Gateway with model number: 4024GZ, and I just installed Ubuntu on it and I am not able to connect to my home's wireless network. I am assuming that this is because of a driver issue, whether there is none or the old driver isn't compatible. So is there a website that I can go to to maybe find a driver that will work with both my wireless card and ubuntu? My wirless network adapter is internal and is a Broadcomm I believe. Any help would be much appreciated.

(btw I am a beginner here and if I have posted this in the wrong section, please forgive me.)

---

### Post by TeoBigusGeekus on 2011-06-05
Have you looked at Additional Drivers (or Hardware Drivers, can't remember) for restricted drivers available for your card?

---

### Post by ssreddy555 on 2011-06-05
Connect to internet with a wire. Then, follow the instructions in this post:
 
[http://ubuntuforums.org/showthread.php?p=10892215#post10892215](http://ubuntuforums.org/showthread.php?p=10892215#post10892215)

---

### Post by suomik1988 on 2011-06-05
> **ssreddy555 said:**
> Connect to internet with a wire. Then, follow the instructions in this post:
 
[http://ubuntuforums.org/showthread.php?p=10892215#post10892215](http://ubuntuforums.org/showthread.php?p=10892215#post10892215)

So everything worked up until the point where I checked the hardware/additional drivers. There was nothing in the list. I entered everything correctly into the terminal per instructions you gave me via the other thread. Did I do something wrong? Or is there one more thing I could check? By the way, when I was able to connect to the internet just fine with the cable, It's just the wireless I'm having trouble with. Thanks for your help so far.

---

### Post by ssreddy555 on 2011-06-06
Have u copied & pasted the first command & clicked Enter? This should have done the update.

After the update is over, have u copied & pasted the second command & hit enter? This should have installed the STA Driver.

Now, if u check in the additional drivers section in the system settings, u will find the STA driver being brought up as a proprietary driver. Activate it & then reboot.

In Ubuntu 11.04, if the driver fails to load in some cases, you may need to reinstall the bcmwl-kernel-source package from Synaptic -> Mark for Reinstallation.

However, only certain models of Broadcom are supported by this driver.  

Supported devices
Driver - Card/Model

STA - BCM4311, BCM4312, BCM4313, BCM4321, BCM4322, BCM43224, BCM43225, BCM43227, BCM43228

b43 - BCM4301 BCM4306/2, BCM4306/3, BCM4311, BCM4312, BCM4318, BCM4320

b43 is also installed along with STA.

For others, u will have to use "ndiswrapper":  

Broadcom BCM4310
Broadcom BCM4311
Broadcom BCM4318
Broadcom BCM4318 HP
Broadcom BCM4318 HP COMPAQ V2415LA
Broadcom BCM4318 HP nx6125
Broadcom BCM94306 Compaq Presario 3160
Broadcom BCM94306MP HP Pavilion ze4560us

Do you know what model is your Broadcom WL adopter?

If not, copy & paste this command in the Terminal & let me know the output:

```
lspci
```

the first letter in the above command is small L (l)not the digit one (1).

---

### Post by axldavis2012 on 2011-06-08
BCM4320 i cant find out whats wrong:(

---

### Post by axldavis2012 on 2011-06-08
i have BCM4320in my hp compaq nx9010 laptop please help i have installed ati and bc installer and something else bc43:(

---

