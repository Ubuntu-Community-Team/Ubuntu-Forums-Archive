---
title: "Help Network manager is gone"
date: 2011-01-29
forum: General Help
---

### Post by G74un3 on 2011-01-29
Sometime in the past week i visited a friend. He had a WEP network  protected by password, Yhe only ptoblem was that he had forgotten the password to his network. This was really anoying and has happened before sp yesterday i decided to install some kind of WEP cracking tool so that it would not happen anymore..

After using sometime without getting anything to work i found this tutorial:

[http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)

 and started following it. i only got to the point where he has updated his computer using update manager and is about to patch his wificard. Then i noticed that the network manager for gnome was gone and the virtualbox logo in my top panel was changed to a red circle with a line running through it.


I have tried to download network manager from another computer and installing it on my laptop but it needs internet to install. Then i tried to connect to my local network using terminal that did't work either i also tried connecting using a cable but had no luck connecting.

The command iwconfig gives me:

```
lo        no wireless extensions.

eth0      no wireless extensions.
wlan0    IEEE 802.11bgn  ESSID:"BA12"        
            Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
            Tx-Power=20 dBm
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off

```I am running maverick meercat on an Asus eee pc s101

I am new to Ubuntu and has only been running it for about a month so please help.

---

### Post by ajgreeny on 2011-01-29
Try 
```
sudo ifconfig eth0 up
sudo dhcpcd eth0
```which may do the trick.  Then install network manager again.

---

### Post by G74un3 on 2011-01-29
Your second command returns:

```
Sudo: dhcpcd: command not found
```...?

---

### Post by ajgreeny on 2011-01-29
Does the first command alone work, or does it throw up any errors.  If no errors, try your network connection again.

---

### Post by G74un3 on 2011-01-30
I have tried plugging my laptop into my wired network and running your first command. Then i tried to install "Network manager for gnome" via "Ubuntu software center" again but it just gives me a messagebox with an error saying 

```
**Failed to download package files.**

Check your internet connection.
```

---

