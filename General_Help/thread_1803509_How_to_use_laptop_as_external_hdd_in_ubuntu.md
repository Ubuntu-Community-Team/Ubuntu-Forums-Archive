---
title: "How to use laptop as external hdd in ubuntu?"
date: 2011-07-13
forum: General Help
---

### Post by DeckerDog97 on 2011-07-13
Hello,
 Just wondering if it was possible to hook up an older laptop of mine to my desktop running Ubuntu 10.10. The laptop is running Xubuntu 10.04, I think. I have a generic wifi card and I can't get the driver working so I would like to install ndiswrapper onto it but I don't have internet on it yet.
Thanks in advance for any help!

---

### Post by seawolf167 on 2011-07-13
The purpose of hooking up the laptop to the desktop is to do what, get an internet connection to download the drivers? Instead of plugging it into your desktop can you plug an ethernet cable from your laptop into your router/gateway and get the internet that way to install the additional drivers?

---

### Post by haqking on 2011-07-13
> **DeckerDog97 said:**
> Hello,
 Just wondering if it was possible to hook up an older laptop of mine to my desktop running Ubuntu 10.10. The laptop is running Xubuntu 10.04, I think. I have a generic wifi card and I can't get the driver working so I would like to install ndiswrapper onto it but I don't have internet on it yet.
Thanks in advance for any help!


you mean you want to use the HDD space in the older machine for storage in your newer one ?

easier to take out the HDD and stick it in a caddy via USB.

Unless you actually want to use the services etc of the other machine

---

### Post by DeckerDog97 on 2011-07-13
It has no ethernet ports and I would like to install ndiswrapper. I tried downloading the files but it wouldn't install. Should I purchase a different wifi card?

---

### Post by haqking on 2011-07-13
> **DeckerDog97 said:**
> It has no ethernet ports and I would like to install ndiswrapper. I tried downloading the files but it wouldn't install. Should I purchase a different wifi card?


OK well i am confused as your title mentions using your old machine as an external HDD, so as i said, why not take it out stick it in a caddy unless you use the machine for other puproses.

So you mean you want to share the HDD out and use it as storage for other machine on the lan ?

---

### Post by DeckerDog97 on 2011-07-13
I still want to use this laptop. I simply want ndiswrapper installed so I can get the wifi card working. I do not have a usb caddy or whatever you mentioned.

---

### Post by seawolf167 on 2011-07-13
You'll need the build-essential package to use ndiswrapper.

[This link ]("http://packages.ubuntu.com/search?keywords=build-essential&searchon=names&suite=all&section=all")has the build-essential packages you can download and move (via flash drive, cd, etc.) to you laptop then install.

[This link ]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing%20Packages%20%28With%20Internet%20access%20on%20another%20computer%29")has the ndiswrapper packages you can download and move (via flash drive, cd, etc.) to you laptop then install.

Here is how to install the build-essential package via the installation cd

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by DeckerDog97 on 2011-07-14
Well, I tried that and it said my driver was invalid. Any other options?

---

