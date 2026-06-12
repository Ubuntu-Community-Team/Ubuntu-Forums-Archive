---
title: "New to ubuntu, need driver help"
date: 2011-08-06
forum: General Help
---

### Post by samc2527 on 2011-08-06
Hi Everyone,

I'm completely new to ubuntu, it's part of an upgrade I'm doing to make an older dell into a HTPC.  That being said I replaced the oem video card with a Nvidia Geforce G100.  When I install the new card ubuntu won't boot and freeze's so I'm assuming I need the drivers however I have no idea how to imstall drivers on ubuntu

Any help is greatly appreciated,

Sam

---

### Post by pqwoerituytrueiwoq on 2011-08-06
what was the old video card/integrated video?
You may need to remove the old driver 1st
boot to recovery mode and drop to root console
```
add-apt-repository ppa:ubuntu-x-swat/x-updates;apt-get update;apt-get install nvidia-current
```
that will install the driver but if you may need to remove a driver first

---

### Post by samc2527 on 2011-08-06
no idea, came standard on a dell optiplex gx620.

---

### Post by pqwoerituytrueiwoq on 2011-08-06
> Integrated Intel® Graphics Media Accelerator 950®; DVI Adapter card; 128MB ATI Radeonª X600SE with DVI and TV -out
256MB ATI Radeon X600 with dual VGA or dual DVIthat is what the specs say i found
did you install any video drivers on the system before now?
if not there is no need to remove any driver just do what i said in post one

---

### Post by samc2527 on 2011-08-06
> **pqwoerituytrueiwoq said:**
> what was the old video card/integrated video?
You may need to remove the old driver 1st
boot to recovery mode and drop to root console
```
add-apt-repository ppa:ubuntu-x-swat/x-updates;apt-get update;apt-get install nvidia-current
```that will install the driver but if you may need to remove a driver first

Ok, but how do I boot to recovery and drop to root console?

Thanks

---

### Post by sinbowden on 2011-08-06
Hello,
Hold down the shift key during bootup, that is if you have only 1 OS installed. At the boot menu, select recovery mode, it should be second or third down on menu. Wait for boot-up processes  to finish after you selected recovery mode. After the initial boot, select (drop to root shell with prompt). Root sell is main admin, this allows you to edit installation, even delete ubuntu so be cautious.

---

### Post by sinbowden on 2011-08-06
> **samc2527 said:**
> no idea, came standard on a dell optiplex gx620.


Integrated Intel Graphics Media Accelator 950 Dynamic Video Memory Technology 3.0

---

### Post by sinbowden on 2011-08-06
> **samc2527 said:**
> Hi Everyone,

I'm completely new to ubuntu, it's part of an upgrade I'm doing to make  an older dell into a HTPC.  That being said I replaced the oem video  card with a Nvidia Geforce G100.  When I install the new card ubuntu  won't boot and freeze's so I'm assuming I need the drivers however I  have no idea how to imstall drivers on ubuntu

Any help is greatly appreciated,

Sam

I have red some more regarding your issue and found a few ways to install video/nvidia drivers:
1.) [http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/](http://www.pendrivelinux.com/installing-proprietary-video-drivers-for-ubuntu/)

2.)[http://news.softpedia.com/news/Install-Nvidia-and-ATI-video-drivers-on-Ubuntu-Edgy-44388.shtml](http://news.softpedia.com/news/Install-Nvidia-and-ATI-video-drivers-on-Ubuntu-Edgy-44388.shtml)

3.)[http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html](http://www.ehow.com/how_5104522_install-video-drivers-ubuntu.html)

I hope one of these links works for you. My apologise for copying and pasting other urls with solutions.

---

