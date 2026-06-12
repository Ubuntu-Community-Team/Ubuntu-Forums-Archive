---
title: "Flash Player problem in Chormium"
date: 2010-08-10
forum: General Help
---

### Post by Weeksy on 2010-08-10
I go to watch youtube within Chromium and I get this message.

[IMG]http://i119.photobucket.com/albums/o157/Weeksy_/screen1.png[/IMG]

Then I go to the link and I get this message.

[IMG]http://i119.photobucket.com/albums/o157/Weeksy_/screen2.png[/IMG]

Can anyone help me?

P.S. I'm using 64-bit version.

---

### Post by MatthewAdams on 2010-08-10
I've always had luck installing "flashplayer-plugin-free" or something along those lines. I'd think for another plugin to work, you'd have to uninstall your previous flash installation. 

Not sure if it supports 64 bit or not though!

---

### Post by luigi_mb on 2010-08-11
Whether you have 32-bit or 64-bit, using Synaptic install "adobe-flashplugin". This is the latest version, which corrects vulnerabilities in the previous versions.

/luigi

---

### Post by FrenchyFungus on 2010-08-11
> **luigi_mb said:**
> Whether you have 32-bit or 64-bit, using Synaptic install "adobe-flashplugin". This is the latest version, which corrects vulnerabilities in the previous versions.

/luigi
I can't find this plugin in synaptic.

---

### Post by lovinglinux on 2010-08-11
See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by techunit on 2010-08-11
You may just need a plug in of some kind I did but I am using Firefox exclusively.

---

### Post by elricscripts on 2010-08-12
Goto the URL: about: plugins
It will probably say you have flash 9.#

Goto:
[http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html)

Download flash 10.1 player for linux.
In the archive will be a libflashplayer.so file.  Move a backup copy of the existing libflashplayer.so out of your chrome plugin folder, then move the new libflashplayer.so there.
Restart chrome

---

### Post by faizal525 on 2010-08-12
> **lovinglinux said:**
> See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Thanx Loving linux! followed the instructions line by line and got it solved both in Chromium and Firefox!

All of you Linux Experts here are beautiful!:D

Cheers!

---

### Post by lovinglinux on 2010-08-12
> **faizal525 said:**
> Thanx Loving linux! followed the instructions line by line and got it solved both in Chromium and Firefox!

All of you Linux Experts here are beautiful!:D

Cheers!

You are welcome.

---

### Post by Crucias on 2010-08-14
Chromium has Flash already inside it, it will always have the latest version, thats one of the bonuses of Chromium.

Unfortunately its not enabled by default.

Right click on your Chromium launch links and hit edit, under command add the extension below and it will work

"--enable-plugins" (without the "")

---

### Post by DarkAmbient on 2010-08-14
Didnt know that their was support for flash from start in chromuim. Good to know!

For what it's worth. I've always just typed this 2 commands into the terminal to get flash to work...

```
sudo apt-get install flashplugin-nonfree
```

then to copy the libflashplayer.so to the chromium plugin folder, type:

```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/chromium-browser/plugins
```

---

