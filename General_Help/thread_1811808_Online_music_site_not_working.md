---
title: "Online music site not working"
date: 2011-07-25
forum: General Help
---

### Post by anshulfy on 2011-07-25
Hi,

I am trying to run online music from the site [http://gaana.com/#/home](http://gaana.com/#/home)  . It has embedded player. But its not working either on mozilla nor on  chrome. Please tell me how should I listen music from this site. Thanks  in advance. Running Ubuntu 10.10.

--
Anshul

---

### Post by seawolf167 on 2011-07-25
Try installing the restricted extras then reloading the page and see if that fixes it

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Bucky Ball on 2011-07-25
Listening to it now using 10.10. Thanks, cool site! I've bookmarked it. ;)

You must be missing some codecs. Not sure what. Try opening Synaptics Package Manager and installing ubuntu-restricted-extras.

I also have VLC installed which drags in codecs. You have flash and java installed?

* Sorry seawolf, you beat me to it. ;)

---

### Post by anshulfy on 2011-07-25
Hi, I have  ubuntu-restricted-extras installed. VLC also I have, flash as well as java also. But I dont know y its not working for me. :(

---

### Post by Bucky Ball on 2011-07-25
Open your Software Sources. Do you have Canonical Partners repo enabled? I also have one called 'Independent'.

---

### Post by anshulfy on 2011-07-25
Yes, I too have canonical partners, from which flash player is installed. Independent also I have.

---

### Post by pqwoerituytrueiwoq on 2011-07-25
which version of firefox and flash?
[http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf](http://www.adobe.com/swf/software/flash/about/flashAbout_info_small.swf)
chrome://browser/content/aboutDialog.xul

---

### Post by Bucky Ball on 2011-07-25
Yes, I right click on the player and one of the options is 'About Adobe Flashplayer' so I'd start looking there.

I like some of the music but the site seems pretty buggy (or could be *my* flash). Plays music fine to begin but then starts to lock up the machine and do strange things at times. I just had to kill firefox from a terminal to get any control as no windows would shut or minimise and I couldn't change tabs in firefox, then the audio kept playing with Firefox shut! So then I had to kill pulseaudio. Weird.

After a song it pops up a window to 'Join Facebook' which you can close. After a couple it pops up a window *demanding* you join Facebook which you *can't *close. Block pop-up windows on that site might avoid this. ;)

---

### Post by anshulfy on 2011-07-25
flash version is 10,2,159,1.

---

### Post by pqwoerituytrueiwoq on 2011-07-26
> **anshulfy said:**
> flash version is 10,2,159,1.
that version is outdated
google flash aid

---

### Post by anshulfy on 2011-07-27
I installed the latest version of flash, but still the problem persists. Current version is 10,3,181,34

---

### Post by anshulfy on 2011-07-28
I don't know how but somehow it started working today........ :) ..

---

