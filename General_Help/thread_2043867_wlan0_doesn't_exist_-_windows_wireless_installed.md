---
title: "wlan0 doesn't exist - windows wireless installed"
date: 2012-08-17
forum: General Help
---

### Post by sefarlow on 2012-08-17
I have a Linksys AE1000 USB wireless adapter. I am running Ubuntu 12.04 LTS. I have installed the proper drive using Windows Wireless drivers and run ndiswrapper. It says hardware detected and I have the wireless icon in top right but not showing any signal. There is no wlan0 device defined so Chrome or Firefox don't pull up any webpages. The adapter uses a Broadcom 4311 chipset. How do I get this thing working? How do I define a wlan0 and tie to the wireless adapter??

---

### Post by efflandt on 2012-08-17
If it uses Broadcom 4311 you may have been better off going to Additional Drivers and trying one or the other of the drivers that suggests.  For one of those drivers instead of showing up as another ethernet device (like eth1) instead of wlan0, but in that case Network Manager still finds it as wireless.  So see what devices show up in **ifconfig -a**

I have never used ndiswrapper because either Ubuntu recognized my wireless automatically, or in the case of Broadcom, one of the suggested drivers worked.

---

### Post by wildmanne39 on 2012-08-17
Hi, ndiswrapper needs to be removed and you do not want to use additional drivers for this card, please do:
```

sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a

```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot
if it does not come on then copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

