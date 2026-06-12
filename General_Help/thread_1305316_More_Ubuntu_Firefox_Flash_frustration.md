---
title: "More Ubuntu/ Firefox/ Flash frustration"
date: 2009-10-29
forum: General Help
---

### Post by GuiGuy on 2009-10-29
I thought that the [advice originally given me by Henrikx]("http://ubuntuforums.org/showthread.php?p=8165085#post8165085") had finally solved my ongoing battle with the Firefox's flash plug in integration 

> 
Download Flashplayer (tar.gz)
[http://get.adobe.com/de/flashplayer/](http://get.adobe.com/de/flashplayer/)

extract tar.gz
copy libflashplayer.so to /home/GuiGuy/.mozilla/plugins
copy libflashplayer.so to /usr/lib/mozilla/plugins (root)
enable JavaScript (Firefox)
restart Firefox


This didn't work initially. However, I worked out (all by myself ;) ) that the Ubuntu upgrade process had installed "/usr/lib/mozilla/plugins/flashplugin-alternative.so". It probably caused a conflict. Once I removed it the Flash non free  plug in worked.

Or so I thought. 

Next reboot and restart of firefox, no flash :?

I checked and made sure libflashplayer.so was present in /usr/lib/mozilla/plugins and /home/GuiGuy/.mozilla/plugins. 

[LIST=1]
[*]On the off chance I re-copied libflashplayer.so from  /home/GuiGuy/.mozilla/plugins to /usr/lib/mozilla/plugins.
[*]I restarted Firefox. Flash was back.
[*]I closed and restarted firefox
[*]No Flash !!?? <grr>
[*]Goto 1
[/LIST]

Can anyone help shed some light on this before I feel inclined to commit myself on the grounds of LMS (Linux Madness Syndrome)

Thanks

---

### Post by LowSky on 2009-10-29
whats wrong with Opera, LOL...

any way what version of Ubuntu are you using 32 or 64 bit?

flash should work with the following command

sudo apt-get install ubuntu-restricted-extras

---

### Post by GuiGuy on 2009-10-29
> **LowSky said:**
> whats wrong with Opera, LOL...

I really liked it. And then I started using it for email. Everytime it checks for mail everything else stops. I gave up. 

> 
any way what version of Ubuntu are you using 32 or 64 bit?


64

> 
flash should work with the following command

sudo apt-get install ubuntu-restricted-extras


Should but doesn't for me. BTW, that install command line is burnt into my brain. I reckon I could type it backwards now, no errors ;).


Cheers

---

