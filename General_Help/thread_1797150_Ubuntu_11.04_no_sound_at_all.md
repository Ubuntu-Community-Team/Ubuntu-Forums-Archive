---
title: "Ubuntu 11.04 no sound at all"
date: 2011-07-04
forum: General Help
---

### Post by pablus89 on 2011-07-04
Hi

[FONT=Lucida Sans Unicode]I instaled Ubuntu 11.04 and noticed there was no sound at all, even after updating the alsa drivers as suggested at [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)[/FONT]

[FONT=Courier New]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update[/FONT]
[FONT=Lucida Sans Unicode]
I also tried reinstalling alsa but it didn't work. alsamixer returns an error regarding the absense 
of such file or path; and the sound preferences show no sound hardware at all. I also tried the 
naive solution of increasing volume levels on both the system and the speakers and it obviously 
didn't work.

My ALSA information is located at:
[http://www.alsa-project.org/db/?f=8bc88da515e55b6a6118fd7f4b1b6a5247e54542](http://www.alsa-project.org/db/?f=8bc88da515e55b6a6118fd7f4b1b6a5247e54542)

Any help is apreciated[/FONT].

---

### Post by CrusaderAD on 2011-07-04
What kind of machine are you running? Did you have sound during the live cd session?

---

### Post by pablus89 on 2011-07-05
Hi,

MSI K9VGM-V board
[http://www.msi.com/product/mb/K9VGM-V.html#?div=Detail](http://www.msi.com/product/mb/K9VGM-V.html#?div=Detail)

AMD X2 64 Dual Core 3800+
Nvidia GeForce 7300GT

I did not try the live cd.

I had 10.04 with sound working.
I made a clean install of 11.04 version.

thanks.

---

### Post by Dio82 on 2011-07-06
Hi, I have the same problem since the last "partial anovation"

This is my Alsa report:[URL="http://www.alsa-project.org/db/?f=7af7507594517c1f5e120da3d33adc6b825b4bd5"] http://www.alsa-project.org/db/?f=7af7507594517c1f5e120da3d33adc6b825b4bd5
[/URL]
Thanks in advance

---

