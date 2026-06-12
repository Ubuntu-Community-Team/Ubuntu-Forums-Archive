---
title: "Exiting Program Kills Network Connection"
date: 2009-07-21
forum: General Help
---

### Post by OpticalEnigma on 2009-07-21
Hi,

So this one has me stumped. I recently switched to CrunchBang Linux 9.04 (another fine Ubuntu derivative running OpenBox) from Ubuntu-EEE 8.04 (Easy Peasy) on my Asus Eee PC 900HA. Though this might not be the most appropriate venue to ask for help, the forums here are always helpful and even a -nudge- in the right direction would be great. 

I finally got Loki Games' Alpha Centauri to install and give me more than one turn of gameplay before crashing and burning ingloriously to the ground. It, however, has managed to get the last word by taking out my networking every time the program exits. At first, I thought this had to do with the crashing of the program, but now that it works and exits successfully it is amazingly still bringing the network down. Being that I'm not nearly the power user that I wish I was, I have no logs to offer you -- yet. However, Conky shows that the network is unavailable and the nm-applet icon just simply disappears. 

Turning on and off the wifi via eeepc-utils turns the light on and off, and the notification still comes up, but still no network. I tried restarting the networking manually via 

```
 sudo /etc/init.d/networking restart 
```

but it doesn't work. 

Any basic ideas I can start with?

---

