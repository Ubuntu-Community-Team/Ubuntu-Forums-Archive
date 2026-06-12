---
title: "Android Tablet Remote Media Control on Ubuntu"
date: 2011-04-22
forum: General Help
---

### Post by Knacker on 2011-04-22
Hi, 
I've been away from linux for a while (it's complicated), but I'm thinking about going back to linux to set up the networked media system of my dreams. 

The thing that I've found amazingly hard to find is a good software solution that would allow me to *fully* remotely control a media player on an ubuntu computer, using an android device. Specifically, what I want to do is control Banshee with an android tablet from within my LAN only. By *fully* control, I don't mean a reduced remote control app that would allow remote tracking, pause/play and volume from android, but rather a solution that would allow me to smoothly use banshee from an android tablet as though I was sitting at my machine. Basically: I want to set up a full-function android tablet remote control for banshee.

I think this should be possible with Android VNC program + ubuntu remote desktop, but I want to know for sure. I want to be able to search my music library in banshee, add a song to a playlist, etc. using the android tablet.  Amazingly, I have not found anything detailing experiences with a setup like this. Is there somehting I'm missing or should this just work (complete with keyboard and mouse shared to android device?)?

Exact versions and devices don't matter as I've not purchased anything yet. Just hypothetically...assuming I have an android tablet and a desktop running ubuntu, both on the same wireless network: how would I do this? 

Would really really *really* rather not be forced any further toward the apple solutions to this -- though it's embarassing how easy it would be to set up with airport, ipad, etc...

Thanks in advance!

---

### Post by bmathis on 2011-04-23
VNC works fine and Remote VNC Pro (free with ads) on the market is great.

There is a remote control app called [Tesla]("http://www.seanhodges.co.uk/index.php?option=com_content&view=article&id=46&Itemid=53") which might be what you're looking for, but I'm not sure if it does everything you want.

---

### Post by Knacker on 2011-04-24
> **bmathis said:**
> VNC works fine and Remote VNC Pro (free with ads) on the market is great.

There is a remote control app called [Tesla]("http://www.seanhodges.co.uk/index.php?option=com_content&view=article&id=46&Itemid=53") which might be what you're looking for, but I'm not sure if it does everything you want.

Thanks for reply and this is good to know. I've read a few positive reports about VNC apps for android, but not many serious reviews that I've found. 

I've found (also only a few) good reports of success with people installing SqueezeBox Server (SBS) and since logitech, who released SBS open source, have also recently offered official "squeezebox controller" app for free in Android Market, I'm considering this combination (app + SBS installed on ubuntu machine) as a way of managing this. 

What is really needed is SSHFS implementation on android. If that existed, the possibilities for playing music remotely would be extraordinary. When I've shown Mac/Windows people what is possible with SSHFS/Fuse and Banshee they've been totally floored, particularly given that implementation of SSHFS on Mac/Win is still so poor. 

In any case, any other thoughts or sugggestions as far as android+ubuntu solutions for remote controlling media playback on a tablet are most appreciated. When I finally find a cheap android tablet to experiment with, I'll post back experiences...

---

### Post by zokama on 2011-05-19
Well, this might be what you called a "*reduced remote control app*" but you could have a go at [SSHmote]("http://www.zokama.com/sshmote"). You can get it from the website or on the android market. The Banshee profile is not included by default but it has DBus support. So I suppose that with minor tweaks on one of the existing profiles (like Kaffeine or Amarok) you should be able to get things working pretty smoothly.

---

