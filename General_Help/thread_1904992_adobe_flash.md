---
title: "adobe flash"
date: 2012-01-05
forum: General Help
---

### Post by blackadam on 2012-01-05
i have adobe flash on linunx i downloaded it off the software center but i still run into this on a few sites where where it says 

"This page requires Javascript, and Adobe Flash version 10.0 or greater. You're seeing this message because you have Javascript disabled in your browser, or because your installed version of Flash does not meet our minimum requirements." 

what can i do to update the flash player? im currently running Linux 11.10

---

### Post by efflandt on 2012-01-05
Install **Ubuntu Restricted Extras** which installs flash, java (openjdk), and other things for multimedia.  That should all be updated automatically when you do regular updates.

---

### Post by Basher101 on 2012-01-05
> **efflandt said:**
> Install **Ubuntu Restricted Extras** which installs flash, java (openjdk), and other things for multimedia.  That should all be updated automatically when you do regular updates.

+1

also brofist on the gtx500 series :D

---

### Post by Frogs Hair on 2012-01-05
If you are using NoScript or something  similar you are probably blocking the ability for java script to work and so the flash version is not being detected . If this is the case select the NoScript icon and temporarily  allow the page and see what happens . If you are using another script blocker , check the settings .  The flash version in the software center is the current stable version and should work .

---

### Post by pqwoerituytrueiwoq on 2012-01-05
are you using no-script if so you need to allow javascript on that site and possibility a 3ed party site

---

### Post by imachavel on 2012-01-05
try opening the terminal ctrl+alt+t

now that you have done so, type in:

sudo apt-get install update

or try sudo apt-get install adobe-flash
or sudo apt-get install flash

make sure you download it first. google adobe flash and when you get to the web site select the linux version for your distro

if that doesn't work google script settings for linux and read thoroughly. these issues can be a pain sometimes

---

