---
title: "Need howto install wireless driver"
date: 2006-02-05
forum: General Help
---

### Post by captainjojo on 2006-02-05
Am new to linux! Am trying to install a Linux driver for my Linksys adaptor, have the driver on disc(at76c503a-cvsroot.tar) but am unable to install. Know how to become the root user have tried to follow instructions from other threads without any success. Get confused in terminal, do you press enter after every line? type anything then press enter? is there someone out there who can help me befor I go totally nuts!!!

---

### Post by jasmuz on 2006-02-05
Just read this: [https://wiki.ubuntu.com/forum/hardware/ndiswrapper]("https://wiki.ubuntu.com/forum/hardware/ndiswrapper")

---

### Post by captainjojo on 2006-02-05
Thanks for the info, helped alot. Installed the windows driver with ndiswrapper but it still does not see my wireless adaptor, is this a network config problem as I cannot find any info on wireless config. also I have a linux driver for the card, would it be better to install this? and if so how do I do this? my linux driver is "at76c503a-cvsroot.tar.gz"

---

### Post by jasmuz on 2006-02-07
That driver means recompiling the kernel wich isnt a good place for a starter...

Did you follow the directions on the page precisely, and did you check the response of the $ sudo lsmod | grep ndiswrapper

please try again until you are certain

Remember....once loaded the ndiswrapper module you must add it to /etc/modules to make it permanent. And once the system sees the ndiswrapper module you might look for a device called 'wlan0' with $ ifconfig   -a

---

### Post by captainjojo on 2006-02-09
Finally got ndiswrapper to work, from the terminal ndiswrapper -l read hardware present and driver present! my problem is now configuring the network. I know this is a very simple task but when you have never done it before !!!

---

### Post by adi-beg on 2006-02-09
System->Administration->Networking, mark wireless, choose properties, write your essid and key, check dhcp. Then open terminal in Applications->Accessories->Terminal
```
sudo gedit /etc/network/interfaces
```
add
```
pre-up modprobe ndiswrapper
post-down rmmod ndiswrapper
```
after line:
```
iface wlan0 inet dhcp
```
and save file.

God luck.

---

