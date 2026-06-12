---
title: "finicky flash player problem"
date: 2010-09-26
forum: General Help
---

### Post by rajohns08 on 2010-09-26
by no means is this a huge problem but its just a small problem ive noticed while on grooveshark or youtube. on grooveshark when i try to drag the volume bar up, whenever i click the volume popout goes away like i clicked through it. on youtube when i try to change the video from 360p to 720p, it pauses the video as if my click went through the video setting popout...anyone else noticed this?

---

### Post by rajohns08 on 2010-09-26
bump

---

### Post by 0N3 on 2010-09-26
What architecture you use 32bit or 64 bit 
try this flash plugin : [https://launchpad.net/~sevenmachines/+archive/flash/+packages](https://launchpad.net/~sevenmachines/+archive/flash/+packages)

Works super for me on Maverick Meerkat both on 32bit and 64bit 64 bit being most problematic for me between the two but seems to be perfect after installing these packages

---

### Post by rajohns08 on 2010-09-26
> **0N3 said:**
> What architecture you use 32bit or 64 bit 
try this flash plugin : [https://launchpad.net/~sevenmachines/+archive/flash/+packages]("https://launchpad.net/%7Esevenmachines/+archive/flash/+packages")

Works super for me on Maverick Meerkat both on 32bit and 64bit 64 bit being most problematic for me between the two but seems to be perfect after installing these packages

how do i found out if im in 32 bit or 64 bit in ubuntu? the weird thing is i KNOW im running 32 bit in windows, but for some reason i think i remember seeing something in ubuntu telling me i was running 64 bit if this is even possible.

---

### Post by rajohns08 on 2010-09-26
> **0N3 said:**
> What architecture you use 32bit or 64 bit 
try this flash plugin : [https://launchpad.net/~sevenmachines/+archive/flash/+packages]("https://launchpad.net/%7Esevenmachines/+archive/flash/+packages")

Works super for me on Maverick Meerkat both on 32bit and 64bit 64 bit being most problematic for me between the two but seems to be perfect after installing these packages


was i supposed to copy/paste this code into terminal? if so here's what happened.

```
 adam@ubuntu:~$ flashplugin64-nonfree (10.2.161.22-0ubuntu0~sevenmachines2) maverick; urgency=low
bash: syntax error near unexpected token `10.2.161.22-0ubuntu0~sevenmachines2'
adam@ubuntu:~$ 
```

---

### Post by efflandt on 2010-09-26
Which Ubuntu version are you actually running and how did you install flash?  I never had any trouble with **flashplugin-installer** (also included in **ubuntu-restricted-extras**) in 64-bit 10.04.  But I got reports of npviewer.bin crashing due to libflashplayer.so segfaulting in 64-bit 10.10.

Uninstalling flashplugin-installer and using most recent real 64-bit flash in either 10.04 or 10.10 did not appear to have any issues.  I got 64-bit flash right from adobe [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

You can tell if your Linux is 64-bit from **uname -a** in a terminal.  If you see **x86_64** it is 64-bit, and if not it is not.

You canNOT install a package by simply typing its name (that is not a valid command), but usually if you download a deb package using Firefox like [https://launchpad.net/~sevenmachines/+archive/flash/+files/flashplugin64-installer_10.2.161.22-0ubuntu0%7Esevenmachines2_amd64.deb](https://launchpad.net/~sevenmachines/+archive/flash/+files/flashplugin64-installer_10.2.161.22-0ubuntu0%7Esevenmachines2_amd64.deb) Firefox would automatically ask if you wanted to install it or save (download) it.  You would have to make sure that you do not have some conflicting flash package already installed.

---

### Post by rajohns08 on 2010-09-26
i dont have this problem using chromium instead of firefox so i suppose im good now.

---

