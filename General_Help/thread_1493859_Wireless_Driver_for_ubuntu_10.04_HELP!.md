---
title: "Wireless Driver for ubuntu 10.04 HELP!"
date: 2010-05-26
forum: General Help
---

### Post by Extract_Here on 2010-05-26
Okay just got a new laptop and i need some help getting my Intel Wifi Link 5100 AGN card to work. Any suggestions? I'm Using ubuntu 10.04 LTS.

---

### Post by bredman on 2010-05-26
Can you explain what you have done already, and why you think your wireless is not working?

You may find this useful...
[http://ubuntuforums.org/showpost.php?p=5754065&postcount=62](http://ubuntuforums.org/showpost.php?p=5754065&postcount=62)

However, this involves building your own drivers, and is 2 years old. I suggest waiting to see if anybody has a more modern (and easy) solution.

---

### Post by philinux on 2010-05-26
> **Extract_Here said:**
> Okay just got a new laptop and i need some help getting my Intel Wifi Link 5100 AGN card to work. Any suggestions? I'm Using ubuntu 10.04 LTS.

I'm assuming you're using the lappy with a wired connection just now.
System>admin>update manager, hit the check button. Do any updates it needs.

Then system>admin>hardware drivers, see if the wireless driver is there. If not even after the update it might now just work.

---

### Post by dino99 on 2010-05-26
install wifi-radar, then
 gksu wifi-radar.

sudo ifconfig wlan0 up
sudo iwlist scan

---

