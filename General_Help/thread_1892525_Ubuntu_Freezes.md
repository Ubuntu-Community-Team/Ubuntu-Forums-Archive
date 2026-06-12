---
title: "Ubuntu Freezes"
date: 2011-12-08
forum: General Help
---

### Post by klereng on 2011-12-08
Hi. 
I've had this problem for a time now and haven't found any solution for it. 
What happens is that when I start up my laptop from hibernation or suspend and sometimes from a fresh reboot it freezes in some kind. It dosent freeze completely, so I can press e.g chrome and its start up, but I cant press any links or start a new program or anything like that. And if I press something in the toolbar e.g the WiFi symbol I can use the links in chrome, but i still hangs.
And Suddenly after anything from 1 minute to 20 minutt everything is okey until next time it goes into suspend or hibernation.

After several weeks of searching the internet I found out that the problem most probably comes from a so called GPU Lockup. And that I need to enable the Intel's own drivers for my graphic card. I found a guide but I'm a really noob with linux so I need some help.

Here is what I found:

[http://drivers.downloadatoz.com/tutorial/22885,how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html](http://drivers.downloadatoz.com/tutorial/22885,how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html)

Step-by-step to Enable Intel Graphics Driver for Ubuntu 10.10:
Install the updated Intel graphics driver by:
```
sudo add-apt-repository ppa:glasen/intel-driver

sudo apt-get update && sudo apt-get upgrade
```
To enable the Intel driver you need to create a file called /var/log/xorg.conf containing the following: 
```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
```

I tried to follow this guide but I cant figure out how I add the xorg.conf file into the var/log folder.

So if anyone could please be so kindly and write me a better step by step guide I would really appreciated it.

My Laptop is by the way is a HP Compaq 6530b, the graphic card is a Intel GMA 4500, and I use ubuntu 11.10

---

### Post by Mark Phelps on 2011-12-08
If you're getting a graphical desktop (and you would say if you were not), the Intel drivers are ALREADY installed.  They get installed when you first setup Ubuntu -- automatically.  There is no need to download or install any other drivers. This is not Windows where you start out by loading drivers; this is Linux, where the drivers get loaded automatically.

---

### Post by klereng on 2011-12-08
> **Mark Phelps said:**
> If you're getting a graphical desktop (and you would say if you were not), the Intel drivers are ALREADY installed.  They get installed when you first setup Ubuntu -- automatically.  There is no need to download or install any other drivers. This is not Windows where you start out by loading drivers; this is Linux, where the drivers get loaded automatically.

Yes, I understand so, but I have a really big problem with my computer that make it almost useless for my schoolwork so I seriously considering to buy a mac. And this is the best solution that I have found, and now I cant do what the guide says. So if you mean that it wont work, maybe you have some ideas of what my problem could be?

---

