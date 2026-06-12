---
title: "How to download from the installation cd"
date: 2010-03-28
forum: General Help
---

### Post by Millnert on 2010-03-28
Hi, I recently installed Ubuntu 9.10 karmic using the .iso file from the official website (burned to a CD) but I have a problem... When I boot into Ubuntu, no drivers are listed for my wireless network (as a matter of fact none are listed when according to the hardware devices :( ). The thing is...

When I use the CD and select "try without changes to computer", Ubuntu detects my proprietary drivers (Broadcom 802.11g network adapter & Broadcom 440x10/100 integrated controller) and allows me to install it (and then restart). 

So my question is, how can I install the proprietary driver to work on Ubuntu (perhaps saving the driver using the CD and allowing the settings to be saved on boot)?

P.S., I can only access internet from Vista & using the installation option 'try without changes to computer' from the CD.

-t.m.

---

### Post by l.billon on 2010-03-28
Hi!
Try uncommenting the CDROM line in
```
/etc/apt/sources.list
```
and updating/upgrading

---

### Post by efflandt on 2010-03-28
Insert install CD, open Synaptic and check the box to add the Ubuntu install CD to the repositories.  Then you may need to hit the refresh button with swirling arrows (ignore errors about internet repositories it cannot access).

But you have not said which Broadcom wireless you have from **lspci** command (BCM43??), so we cannot tell if you need bcmwl-kernel-source or b43-fwcutter package.

---

### Post by Millnert on 2010-03-28
Ok, so right now I'm on the internet via the Installation cd! But I want some clarification as to what I am supposed to do in order to get this working (internet) without the cd. 

I don't know how to uncomment the source.list file since in the getedit I don't see such a line...

From the lspci it states that I have a Broadcom Corp. BCM 802.11B/G network card. When opened the hardware devices, the cd it says I can activate Broadcom b43 wireless driver (fw cutter) and Broadcom STA wireless driver. Since I installed the prior I have the internet running, but the question is still how it work without the cd (or basically use the downloaded driver from the cd on the on the installed Ubuntu since I that is what I can boot in without the cd.) ?

---

### Post by coffeecat on 2010-03-28
Have a look at efflandt's post again. Boot up from your installed Ubuntu. **Then**, insert the live CD, open Synaptic.... and so on. That way you can install the Broadcom packages which are on the CD to your hard drive install.

---

### Post by Millnert on 2010-03-28
Good news, all is well thanks to **coffeecat** &** efflandt**!!!:popcorn: I thank you guys for the advice and want to say thank you for your help! See you around;)

---

