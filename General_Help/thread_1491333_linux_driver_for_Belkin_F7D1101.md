---
title: "linux driver for Belkin F7D1101"
date: 2010-05-23
forum: General Help
---

### Post by Don10 on 2010-05-23
Belkin does not have a driver for linux, need a driver.  Thank you

Don

---

### Post by talcottenator on 2010-06-04
i am experiencing the same problem. i searched for linux compatible wireless cards and found some lists of devices/chipsets known to be compatible w/ linux. But this seemed very limited and having already purchased this wireless usb stick would like to find out if it can be made to work.

---

### Post by qwerty2009 on 2010-06-04
i got my belkin adapter working by installing the following from synaptic > linux-backports-modules-wireless-lucid-generic
or you can type the following into terminal> sudo apt-get install linux-backports-modules-wireless-lucid-generic

---

### Post by aptdude on 2010-06-06
howdy,  I tried your apt-get on ubuntu desktop 10.04 lts, and it did install three packages, but I don't have a wlan0 on this device.  Is there another series of commands or edits that you performed, qwerty2009?
tia --

---

### Post by diablo75 on 2010-06-06
Hey everyone!

I just popped in here to say I just helped someone get this particular adapter working.

We didn't test WPA out, as the connection he wanted to establish was to an unsecured network, but it did work like a charm.

He basically did all the hard work for me and I found that the mistake he made was in selecting the wrong inf file for ndiswrapper to use to install the driver for the adapter.  When you browse the install CD that comes with the Belkin USB adapter, you will come to several folders that relate to the version of Windows.  There is one version folder that's called XP2K.  He had originally tried to use the "Vista32" drivers, which LOOKED like they had installed correctly, but according to the log file, it really didn't.  I found that removing the vista driver and installing the XP2K driver instead solved the problem.

Just dropping this by in case anyone else out there is still having trouble.

---

### Post by linux.is.skynet on 2010-06-07
Yeah, it doesn't work on unsecured networks :(

---

### Post by fgsupport on 2010-06-19
Try going to Belkin and downloading the Windows driver and save it. Download Wine and run the .exe file. Then see if the wireless works. If it does than you can uninstall Wine if you want. This method worked on 8.04.

---

### Post by Xelator23 on 2012-01-21
Hi

Wher is must install the Driver all time wenn i will it install i get an 1627 Error.

I use Kubuntu 11.10

cu

---

### Post by nothingspecial on 2012-01-21
Hi,

Rather than post your question in a really old thread, please make a thread of your own with as much detail of your problem as you can.

Closed.

---

