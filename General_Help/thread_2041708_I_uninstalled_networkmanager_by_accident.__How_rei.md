---
title: "I uninstalled networkmanager by accident.  How reinstall without connection?"
date: 2012-08-13
forum: General Help
---

### Post by ThreeOwls on 2012-08-13
Hello.  Fist off, let it be known that I have a dual-boot computer running Windows 7 OS and Ubuntu 12.04 LTS OS.   

I was playing around and looking at things to install in the Synaptic Package Manager.  I tried installing a notification app for network and in doing so it wiped out and uninstalled the reliable and always working "networkmanager" program that comes by default in the OS.   The thing is, my computer at this time relies on a WiFi connection for the internet.   Without the NetworkManager installed and available, I am completely unable to download it and reinstall it again in the Synaptic Package Manager. 

As I said, I have access to Windows 7 and its WiFi connection still works perfectly on that side.   Is there a way to download the "networkmanager" program.  If so, how do I fully install it in the terminal. (I have a feeling that the Ubuntu Software Center program will not allow me to install it through it so I have to rely on terminal to install).  Does one have to download and install more than the DownloadManager program?

Also, does anyone know the terminal command to get NetworkManager to startup and run?   Thanks for reading and the time.

---

### Post by Tobeus on 2012-08-13
I believe the terminal command to get network manager to start is:

```
sudo service network-manager start
```If it doesn't work you could open a terminal windows and try these:

```
sudo ifconfig wlan0 up
sudo dhclient wlan0
```If that brings up the network with the existing configuration, you should be able to reinstall with:

```
sudo apt-get update
sudo apt-get install --reinstall network-manager network-manager-gnome
```Good luck!

-Tobeus

---

### Post by steeldriver on 2012-08-13
if you really uninstalled (as opposed to just disabling) network-manager, then you could always use the /etc/network/interfaces file to define a temporary interface via the older networking service - that would allow you to get online and reinstall n-m

imo that would be much easier than downloading the correct deb via windows (although that's an option as well)

---

### Post by Habitual on 2012-08-13
the .deb(s) "*may*" be in /var/cache/apt/archives

terminal > 
```
ls -al /var/cache/apt/archives/net*m*
```

If they are...
sudo dpkg -i /var/cache/apt/archives/network-manager 
sudo dpkg -i /var/cache/apt/archives/network-manager-gnome

Good Luck.

---

