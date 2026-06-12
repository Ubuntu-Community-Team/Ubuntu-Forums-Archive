---
title: "Soundcard/DVD player?"
date: 2006-02-14
forum: General Help
---

### Post by RecedingLight on 2006-02-14
I just installed ubuntu yesterday afternoon on a Intel Pentium 2 IBM Thinkpad. I cannot play a DVD or listen to CDs at all. I looked in the sound options, and there is no soundcard installed apparently. The DVD player is a Toshiba DVD-ROM SO-C2102. How would I go about fixing these errors?

---

### Post by Iandefor on 2006-02-14
[quote=RecedingLight]I just installed ubuntu yesterday afternoon on a Intel Pentium 2 IBM Thinkpad. I cannot play a DVD or listen to CDs at all. I looked in the sound options, and there is no soundcard installed apparently. The DVD player is a Toshiba DVD-ROM SO-C2102. How would I go about fixing these errors?[/quote] What's your sound card?

---

### Post by learning curve on 2006-02-14
wget [http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.4-2_i386.deb)
sudo dpkg -i automatix-ubuntu_4.4-2_i386.deb

Copy and paste the above into the terminal and run Automatix.  It will be in Applications/System Tools after it has been installed.  You will find the Codecs for your DVD's as well as many other useful tools.  As far as your sound, you probably have a built in soundcard on that thinkpad.  When Ubuntu is loading does it say setting up ALSA(sound card)?  See if it sets it up or not first.  You may be able to find a linux driver on the forum if you go to the website for IBM and try to find out what the soundcard is.:cool:   Good Luck!

---

