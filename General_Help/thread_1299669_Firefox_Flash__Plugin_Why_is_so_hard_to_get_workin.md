---
title: "Firefox Flash  Plugin: Why is so hard to get working?"
date: 2009-10-24
forum: General Help
---

### Post by GuiGuy on 2009-10-24
As I've come to expect with every Linux update, the Flash plug in no longer works in Firefox. 

about: plugins tells me
> 
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


Flash does, of course, work in other browsers like Konqueror so I figure it has to be installed. 

Anyone got any useful tips or ideas that might help me sort this out?

PS: I have tried removing every other plug in and add-in, including adblock. It didn't help.

TIA

---

### Post by Henrikx on 2009-10-24
Download Flashplayer (tar.gz)
[http://get.adobe.com/de/flashplayer/](http://get.adobe.com/de/flashplayer/)

extract tar.gz
copy libflashplayer.so to /home/GuiGuy/.mozilla/plugins 
copy libflashplayer.so to  /usr/lib/mozilla/plugins (root)
enable JavaScript (Firefox)
restart Firefox

---

### Post by 3rdalbum on 2009-10-24
Try removing (renaming) your Firefox profile from inside ~/.mozilla.

If Firefox can find the plugin, then there's no reason why it shouldn't be able to be used unless you have some sort of odd setting turned on that stops plugins working.

---

### Post by GuiGuy on 2009-10-24
> **Henrikx said:**
> Download Flashplayer (tar.gz)
[http://get.adobe.com/de/flashplayer/](http://get.adobe.com/de/flashplayer/)

extract tar.gz
copy libflashplayer.so to /home/GuiGuy/.mozilla/plugins 
copy libflashplayer.so to  /usr/lib/mozilla/plugins (root)
enable JavaScript (Firefox)
restart Firefox

Thank you. I can also see now what happens; the upgrade process installs "/usr/lib/mozilla/plugins/flashplugin-alternative.so". This probably caused a conflict. I had to remove it to make the plug in work. 

Again, many thanks.

---

### Post by GuiGuy on 2009-10-24
> **3rdalbum said:**
> Try removing (renaming) your Firefox profile from inside ~/.mozilla.

If Firefox can find the plugin, then there's no reason why it shouldn't be able to be used unless you have some sort of odd setting turned on that stops plugins working.

Thanks for the reply. Henrikx suggestion worked as it made me see there was a conflicting file. 

Cheers

---

### Post by GuiGuy on 2009-10-25
AFter Flash was working yesterday, I switched the PC off last night. 

This morning, restarted. No Flash!!??

Checked & confirmed that everything was in place as per Henrikx's suggestions, which had it working yesterday. 

Restarted Firefox. No good. No Flash :confused:

**Gave up. Installed Opera. I like it!!**

---

