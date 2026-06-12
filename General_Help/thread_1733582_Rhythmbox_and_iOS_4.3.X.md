---
title: "Rhythmbox and iOS 4.3.X??"
date: 2011-04-19
forum: General Help
---

### Post by turqoisehex on 2011-04-19
After updating my 3GS iPhone to 4.3, I'm no longer able to sync music to it, or mount it at all.

I've followed the instructions at [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone), but no luck so far. libimobiledevice1 is installed (it was already installed) and I don't know what else to do. Any help is much appreciated.

Thanks!:p

---

### Post by oracle2b on 2011-04-19
> sudo add-apt-repository ppa: pmcenery/ppa
sudo apt-get update
sudo apt-get install libimobiledevice1

Now, plug-in your iphone and it should appear in gtkpod(Rhythmbox):

P.S remove the space between "ppa: & pmcenery/ppa" THe formatting made it into a smiley face.

---

### Post by turqoisehex on 2011-04-20
:guitar:
Thank you SO MUCH!

I hope they update the repositories version to 1.0.6 soon so others don't have the same problem! 
(...that is, the 5 or 6 other people who have linux on their computer but apple on their phone :KS)

UPDATE:
I still wasn't able to sync music to my phone, so I did:

> sudo apt-get install ifuse gtkpod mp3gain faad faac lame gtkpod-data id3v2 libid3-3.8.3c2a libmp4v2-0 vorbis-tools (gtkpod probably would have been sufficient)

I rebooted, and sync worked perfectly. I love this community ^__^

---

