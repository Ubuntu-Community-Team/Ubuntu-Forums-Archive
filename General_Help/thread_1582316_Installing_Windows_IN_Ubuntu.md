---
title: "Installing Windows IN Ubuntu"
date: 2010-09-26
forum: General Help
---

### Post by Dyffo on 2010-09-26
Is it possible to install Windows within Ubuntu, not using Virtual box or any other derivative.
I am a 100% committed UBUNTU user, however I need to install a USB wireless adapter and a USB internet Dongle Modem.
I live in Portugal and the only devices that I can obtain call for Windows to do the installation. If possible I don't want to install Ubuntu within Windows, I have had this configuration before and I found it troublesome - not least with Virus problems and continuous upgrades.

---

### Post by raafaell on 2010-09-26
> **Dyffo said:**
> Is it possible to install Windows within Ubuntu, not using Virtual box or any other derivative.
I am a 100% committed UBUNTU user, however I need to install a USB wireless adapter and a USB internet Dongle Modem.
I live in Portugal and the only devices that I can obtain call for Windows to do the installation. If possible I don't want to install Ubuntu within Windows, I have had this configuration before and I found it troublesome - not least with Virus problems and continuous upgrades.

There may be a way to do that, but I have searched for that and could not found, you can install '**wine**' for running windows softwares in Ubuntu..

---

### Post by searchfgold6789 on 2010-09-26
...I don't think there is a way to do that!

---

### Post by raafaell on 2010-09-26
> **searchfgold6789 said:**
> ...I don't think there is a way to do that!

That's what I think too.. as I couldn't find anything on doing that.

---

### Post by sendblink23 on 2010-09-26
is any of those devices recognized inside Ubuntu?

tons of wireless & modem USB devices work fine


My question is what are you planing to do with those devices?

---

### Post by gypsumwolf on 2010-09-26
> **Dyffo said:**
> Is it possible to install Windows within Ubuntu, not using Virtual box or any other derivative.
I am a 100% committed UBUNTU user, however I need to install a USB wireless adapter and a USB internet Dongle Modem.
I live in Portugal and the only devices that I can obtain call for Windows to do the installation. If possible I don't want to install Ubuntu within Windows, I have had this configuration before and I found it troublesome - not least with Virus problems and continuous upgrades.

You do have USB support with Virtual Box from Sun, not the OSE version that Ubuntu has in the repos. Why not Virtual Box?

---

### Post by Dyffo on 2010-09-26
> **sendblink23 said:**
> is any of those devices recognized inside Ubuntu?

tons of wireless & modem USB devices work fine


My question is what are you planing to do with those devices?

In Both cases it is for Remote Internet connection. Here in Portugal the Suppliers like Vodafone do not market a Linux version. The software just will not work. The Wireless USB is an SMC device.Again the Software will not work

---

### Post by Dyffo on 2010-09-26
> **gypsumwolf said:**
> You do have USB support with Virtual Box from Sun, not the OSE version that Ubuntu has in the repos. Why not Virtual Box?

I know there is USB support from V.B. but the Software for these devices will not install or run on V.B.

---

### Post by sendblink23 on 2010-09-26
> **Dyffo said:**
> In Both cases it is for Remote Internet connection. Here in Portugal the Suppliers like Vodafone do not market a Linux version. The software just will not work. The Wireless USB is an SMC device.Again the Software will not work

[Did you google for Ubuntu vodafone]("http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=go#sclient=psy&hl=en&q=ubuntu+vodafone&aq=f&aqi=g4g-o1&aql=&oq=&gs_rfai=&pbx=1&fp=8d9c50a61d5b9175")? Maybe there is a different solution

---

### Post by WorMzy on 2010-09-26
You can't install Windows inside Ubuntu without a virtual machine for the simple reason that Windows is not a Linux application. ;)

If you have the Windows driver, and an .inf file to go with it, then you can install the driver for the wireless USB stick with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). Not sure about the modem.

---

### Post by Dyffo on 2010-09-29
> **WorMzy said:**
> You can't install Windows inside Ubuntu without a virtual machine for the simple reason that Windows is not a Linux application. ;)

If you have the Windows driver, and an .inf file to go with it, then you can install the driver for the wireless USB stick with [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). Not sure about the modem.

All done and Working - also get my webcam to work on Skype.

---

