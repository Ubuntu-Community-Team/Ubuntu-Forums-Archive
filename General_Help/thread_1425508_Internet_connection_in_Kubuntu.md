---
title: "Internet connection in Kubuntu"
date: 2010-03-09
forum: General Help
---

### Post by jre6 on 2010-03-09
How can I connect my computer to the internet through Kubuntu 9.04? I will use a dial-up connection to do this and my computer has a Conexant HDA modem. And, by any case, if I happen to use a mobile broadband service to connect to the internet, will the USB dongle (most probably Huawei EC1260 will be provided if I subscribe to a mobile broadband service) provided for this purpose work out-of-the-box in Kubuntu as it works in Ubuntu? If it does not work out-of-the-box, what should I do?

---

### Post by bobcollard on 2010-03-09
> **jre6 said:**
> How can I connect my computer to the internet through Kubuntu 9.04? I will use a dial-up connection to do this and my computer has a Conexant HDA modem. And, by any case, if I happen to use a mobile broadband service to connect to the internet, will the USB dongle (most probably Huawei EC1260 will be provided if I subscribe to a mobile broadband service) provided for this purpose work out-of-the-box in Kubuntu as it works in Ubuntu? If it does not work out-of-the-box, what should I do?
You need PPPconfig.  It may not be installed, check in Synaptic Package Manager.  If it is installed open Terminal and enter ```
sudo pppconfig
``` that should get you started.

---

### Post by jre6 on 2010-03-10
> **bobcollard said:**
> You need PPPconfig.  It may not be installed, check in Synaptic Package Manager.  If it is installed open Terminal and enter ```
sudo pppconfig
``` that should get you started.
There is no application named Synaptic Package Manager in Kubuntu. Are you talking about KPackageKit, the package manager of KDE? And, pppconfig is a Gnome package, so will it work in KDE?

---

### Post by bobcollard on 2010-03-10
> **jre6 said:**
> There is no application named Synaptic Package Manager in Kubuntu. Are you talking about KPackageKit, the package manager of KDE? And, pppconfig is a Gnome package, so will it work in KDE?
Using kpackagekit install synaptic.  It's a better Package Manager.  Since kubuntu is based on Ubuntu with KDE as the desktop, yes it will work just fine.

---

### Post by jre6 on 2010-03-11
Two more questions:
1)If I use a mobile broadband device, will the USB dongle (most probably Huawei EC1260) work in Kubuntu? How will I configure it?
2)A question about Ubuntu: I have a Conexant HDA modem. I have followed all the instructions on the page: [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant), but after this the osservices.h error appears. I have circumvented this issue, but after this, when I execute sudo /usr/sbin/hsfconfig , the sound becomes disabled and the modem is also not installed. I use gnome-ppp as the dialer. Please help.

---

### Post by bobcollard on 2010-03-11
> **jre6 said:**
> Two more questions:
1)If I use a mobile broadband device, will the USB dongle (most probably Huawei EC1260) work in Kubuntu? How will I configure it?
2)A question about Ubuntu: I have a Conexant HDA modem. I have followed all the instructions on the page: [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant), but after this the osservices.h error appears. I have circumvented this issue, but after this, when I execute sudo /usr/sbin/hsfconfig , the sound becomes disabled and the modem is also not installed. I use gnome-ppp as the dialer. Please help.
Sorry this is over my head.  Know nothing about dongles or the second problem. Perhaps it would be better to divide these up and make new threads so they can be answered one at a time.  That is how the forum is set up.

---

