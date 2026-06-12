---
title: "Acer Aspire One-Wubi Install-No Wirless"
date: 2010-03-16
forum: General Help
---

### Post by zazen666 on 2010-03-16
HI,

Just got a Acer Aspire one D240-Ks113 model # KAV60.

No cd slot, and I dont have access to install from usb, so I used the Wubi, which installed  latest Ubuntu network remix. So easy and no need to mess with partition. Been a few years since I used Ubuntu and was glad to have something like that.

However, no wireless. How do I get it up and running?

---

### Post by spiderbatdad on 2010-03-16
do you know the wireless card? Either broadcom or atheros. The atheros should work by default...depending on the next question...the version of ubuntu/wubi installed?
Sorry I have never used wubi, but these questions should help to discover an answer.

---

### Post by zazen666 on 2010-03-16
ubuntu version 9.10
wubi versionn cant find, but it is latest.

wirles card broadcom.

And im pretty sure its not working by default. it doesnt find a signal at all, despite other computers workign fine.

thanks

---

### Post by spiderbatdad on 2010-03-16
right. the broadcom would not work by default, only the atheros. Broadcom requires a proprietary driver. Possibly this is offered in System>>Administration>>Hardware Drivers...or a better choice might be the broadcom-sta (or whatever it is) in synaptic package manager. You would need a temporary wired connection to download either driver. There is some good community documentation on the Acer Aspire One:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
That should help to get you going.

A little further investigation suggests the broadcom-STA may cause problems in Karmic but is working for Lucid...maybe you want to upgrade? The bcmwl driver is recommended for this card using karmic, as near as I can tell.

---

### Post by zazen666 on 2010-03-16
nood questions: going to synaptic package manager only shows me currently installed packages? how to I find the broadcom?



(its not in hardware drives anyways)

edit: scratch that dumb questions

---

### Post by mcoleman44 on 2010-03-16
sudo apt-get update
sudo apt-get upgrade

May take a while but when you restart go to system>admin>hardware drivers and install the STA wireless driver.

It works fine for me in karmic.

Ohh, and you normaly have to restart after a second time after install for synaptic's to work and show you all the packages. Or you could just do it through a terminal and type what I mentioned above.

---

### Post by zazen666 on 2010-03-16
Well, that seemed to do it. A reset tunred the light on then I had to click uptop to manually extablish connection, but seems to work.

Thank you very very much, much appericated.

---

