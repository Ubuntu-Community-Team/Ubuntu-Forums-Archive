---
title: "Complete System Freeze"
date: 2012-05-30
forum: General Help
---

### Post by ShareBuntu on 2012-05-30
I've had some issues recently on Chromium (v21) where Adobe Flash would make the entire system freeze up. At least, I think it's Flash. I have a Nvidia GTX 260 card.

I have no idea why this is happening, but I'm curious, are there things I can do maintenance-wise after I have to press the power button to reboot from a full system freeze? I'm a bit paranoid of damaging my install.

---

### Post by stonewall264 on 2012-05-30
There seems to be a bug in 12.04 relating to NVIDIA hardware and Flash Player (blue colors, crashing, etc.) I was having the same freezing problems, the solutions in [this]("http://askubuntu.com/questions/117127/flash-video-appears-blue") Ask Ubuntu mostly fixed the problem. I installed the modified VDPAU driver according to these instructions:

sudo add-apt-repository ppa:tikhonov/misc
sudo apt-get update
sudo apt-get install libvdpau1

Then reboot.

No more system freezes anymore.

---

### Post by ShareBuntu on 2012-05-31
> **stonewall264 said:**
> There seems to be a bug in 12.04 relating to NVIDIA hardware and Flash Player (blue colors, crashing, etc.) I was having the same freezing problems, the solutions in [this]("http://askubuntu.com/questions/117127/flash-video-appears-blue") Ask Ubuntu mostly fixed the problem. I installed the modified VDPAU driver according to these instructions:

sudo add-apt-repository ppa:tikhonov/misc
sudo apt-get update
sudo apt-get install libvdpau1

Then reboot.

No more system freezes anymore.
Thanks for this! I installed libvdpau1 from that PPA. I had one freeze after that, however, I didn't have the mms.cfg file in /etc/adobe. I've enabled that now too, so I'll keep an eye on it.

Do you know the difference between flashplugin-installer and adobe-flashplugin in the repositories?

---

### Post by stonewall264 on 2012-05-31
From what I understand, adobe-flashplugin actually contains the Flash plugin itself, while flashplugin-installer fetches it during the install (probably because it's not open source).  Not sure which one is better, I had the same freezing problems using both methods.

After doing the VDPAU fix, I still had the system freeze once (shortly after posting this fix), but the stability has improved considerably.

---

### Post by ShareBuntu on 2012-06-01
> **stonewall264 said:**
> From what I understand, adobe-flashplugin actually contains the Flash plugin itself, while flashplugin-installer fetches it during the install (probably because it's not open source).  Not sure which one is better, I had the same freezing problems using both methods.

After doing the VDPAU fix, I still had the system freeze once (shortly after posting this fix), but the stability has improved considerably.
I tried the "Prevent Flash Player from finding libvdpau" fix posted on the link you gave and it seemed to have worked. I had one more crash after that, but stability has improved significantly. Last resort is to disable Flash's hardware acceleration.

---

