---
title: "display reduces to 1 line"
date: 2011-02-06
forum: General Help
---

### Post by qbektrix on 2011-02-06
I am using Ubuntu live on a i7 x64 with Zotac nvidia. Not sure if Ubuntu started the issue.

When I am using the PC, suddenly the whole display goes blank except for one horizontal line. Even when I restart, the same line will be only visible.

Then I have to wait for sometime with the PC shutdown. After which the whole display will be back. Not sure what is causing the issue.

I suspect its an issue with the graphics card. But just want to know if ubuntu is contributing to the issue in any way.

---

### Post by matt_symes on 2011-02-06
Hi

Is it overheating ?

Kind regards

---

### Post by qbektrix on 2011-02-06
> **matt_symes said:**
> Hi

Is it overheating ?

Kind regards

There is about 3 fans in the case. I am using cooler master Nvidia case. So, I am hoping that heat is not the issue here. How can I find it???

---

### Post by pqwoerituytrueiwoq on 2011-02-06
have the right driver installed?
nrv reread post you are runnuing a live cd so no 
but the driver is probably why there is a issue
incorrect driver is probably heating it up a lot

---

### Post by matt_symes on 2011-02-06
Hi

Install lm-sensors and run the configuration. For a graphical panel app install GNOME Sensors Applet 2.2.3 as well.

```
sudo apt-get install lm-sensors
sudo apt-get install sensors-applet
``` 

Check the boards are seated correctly and there are no loose cables

Kind regards

---

### Post by qbektrix on 2011-02-06
> **matt_symes said:**
> Hi

Install lm-sensors and run the configuration. For a graphical panel app install GNOME Sensors Applet 2.2.3 as well.

```
sudo apt-get install lm-sensors
sudo apt-get install sensors-applet
``` 

Check the boards are seated correctly and there are no loose cables

Kind regards

Can I do these, if I am using ubuntu from a live cd???

---

### Post by matt_symes on 2011-02-06
Hi

As far as i am aware, yes, but the changes will not be persistent.

Kind regards

---

