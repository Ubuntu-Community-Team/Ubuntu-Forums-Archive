---
title: "Wireless adapter issues"
date: 2010-03-19
forum: General Help
---

### Post by totalSKID on 2010-03-19
Hi,
I have just installed ubuntu 9.10 and I am having difficulties connecting to my wireless network.  I completely new to any Linux os and really have no idea whats going on.  I have only started to figure out how the terminal works. 

Anyway, I have a Linksys WUSB600N USB adapter which i have heard doesnt work with ubuntu as soon as it is installed.  It lets me see the list of available networks, but when connect to one and input the correct WEP key, it just tries to connect for a minute or 2 and then asks for the key again.  I have tried the key in both WEP options it has as i dont know which is the correct one, but neither work anyway.

Any help would be much appreciated.

---

### Post by Bucky Ball on 2010-03-19
Have you plugged in an ethernet cable and gotten all updates? This might load a restricted driver you are missing.

System->Admin->Hardware Drivers. Anything there regarding wireless and disabled?

Plug in an ethernet cable if you can and boot with it plugged in.

---

### Post by gadolinio on 2010-03-19
I had a similar problem with an asus eeepc 1201N. It could show the connections, but after trying for a couple of minutes it dropped, and finally couldn't connect. I solved it by installing a driver i downloaded from launchpad. I found the driver by looking for wireless issues with my netbook model; then i found the exact wireless card model. It wasn't a very user-friendly job, but in the end it worked out perfectly.
So all i can tell you is to look for the computer and wifi card's name, and see if there are any drivers for it.
Hope you find this somewhat useful at least...

---

### Post by totalSKID on 2010-03-20
Thanks for the help, I did use a wired connection to download updates which i am not sure were necessary because it didnt work until I followed the advice here from another thread:

> **chili555 said:**
> Oh, my oh my, yes! Here is your device:Both rt2800usb and rt2870sta claim this device:As you can see from your *dmesg*, the only thing worse than having no driver is having two conflicting drivers fighting. Let's try to fix it:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot. Is your wireless working?

The problem was fixed as simple as that after a package was automatically downloaded when i connected with an ethernet cable; again, I do not know if it made a difference.  Hopefully this will help anyone else with this problem.

---

### Post by gadolinio on 2010-03-20
Great! Enjoy it!

---

