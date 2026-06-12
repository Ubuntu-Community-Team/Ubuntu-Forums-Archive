---
title: "Adobe Flashplayer 10 problem"
date: 2010-11-17
forum: General Help
---

### Post by Ghost_Mazal on 2010-11-17
Lo all ,
 
I have a problem with Adobe Flashplayer 10. It seems to be incompatible with a countdown timer on a specific site. I use firefox and when I open the site firefox freezes , hangs for a while and then I get an Adobe flashplayer 10 error stating the script encountered a problem. This is how and know the problem is the adobe flash and I know it is with that countdown timer as it only started when that was added to the site. Obviously it is a compatibility problem as it doesn't hapen on my Windows pc.
 
My question is two parts: a. Is there another flash player I can try with Firefox and b. If yes How do I uninstall the Adobe Flashplayer and install the other one.
 
Ubuntu 10.04.1 64 bit with all latest automatic updates , browser is Firefox.
 
Thanx for any help.

---

### Post by gandaran on 2010-11-17
> **Ghost_Mazal said:**
> Lo all ,
 
I have a problem with Adobe Flashplayer 10. It seems to be incompatible with a countdown timer on a specific site. I use firefox and when I open the site firefox freezes , hangs for a while and then I get an Adobe flashplayer 10 error stating the script encountered a problem. This is how and know the problem is the adobe flash and I know it is with that countdown timer as it only started when that was added to the site. Obviously it is a compatibility problem as it doesn't hapen on my Windows pc.
 
My question is two parts: a. Is there another flash player I can try with Firefox and b. If yes How do I uninstall the Adobe Flashplayer and install the other one.
 
Ubuntu 10.04.1 64 bit with all latest automatic updates , browser is Firefox.
 
Thanx for any help.

how did you install it? the 'flashplugin-installer' package from package manager? if so then use the package manager to remove it.
the system installed flash is 32-bits so for 64-bits flash it's best to use the flash-aid addon for firefox, the addon removes the installed flash and installs the 64-bits flash and keep it updated, try it!
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Ghost_Mazal on 2010-11-17
Nope I didn't install it myself with package manager. I don't know how or when it got installed. Will try that thank you

---

### Post by Ghost_Mazal on 2010-11-17
Tried that firefox plugin. Installed the 64bit flash with that plugin. It didn't help. Problem is still the same. I also went and check in synaptic and flashplugin installer wasn't installed. I installed that to try that , but that also didn't work.

Flash not working on 10.04 64bit :(

Anything else I can try ?

---

### Post by Ghost_Mazal on 2010-11-17
Tried flashplugin nonfree as well. Also doesn't work.

---

### Post by gandaran on 2010-11-17
post the link to the problem website so someone with 64-bits flash can check.

---

### Post by Ghost_Mazal on 2010-11-17
[http://www.granturismo.co.za](http://www.granturismo.co.za)

---

### Post by krismatth3 on 2010-11-17
Well, it works in 64 bit chrome with the beta linux flash player. :) After you download the beta flash player from adobe, 

```

# sudo mkdir /opt/google/chrome/plugins
# sudo cp libflashplayer.so /opt/google/chrome/plugins

```

---

### Post by gandaran on 2010-11-17
> **Ghost_Mazal said:**
> [http://www.granturismo.co.za](http://www.granturismo.co.za)
the countdown timer I think is a java applet not flash (I could be wrong) which java do you have installed sun-java or openjdk-java?

---

### Post by Ghost_Mazal on 2010-11-17
The error comes specificly from Adobe Flash Player , thats what crash and gives the error message.

According to Synaptic there is quite a few Java's installed. OpenJDK 6 is one of them. Don't see a Sun Java on the list

---

### Post by dehash on 2010-11-17
> **Ghost_Mazal said:**
> [http://www.granturismo.co.za](http://www.granturismo.co.za)

I get a timeout unresponsive script pop up from the adobe flash player on that page on 32bit Ubuntu Firefox 3.6 Flash player 10.1.

Suggests to me the issue is triggered by the Actionscript in the swf.

---

### Post by Ghost_Mazal on 2010-11-17
> **dehash said:**
> I get a timeout unresponsive script pop up from the adobe flash player on that page on 32bit Ubuntu Firefox 3.6 Flash player 10.1.

Suggests to me the issue is triggered by the Actionscript in the swf.

That's greek to me ?

---

### Post by gandaran on 2010-11-17
> **Ghost_Mazal said:**
> The error comes specificly from Adobe Flash Player , thats what crash and gives the error message.

According to Synaptic there is quite a few Java's installed. OpenJDK 6 is one of them. Don't see a Sun Java on the list
well it could be flash embedded in java, I said it wasn't flash because it doesn't say anything about flash if you right click the timer applet.
but try installing sun-java6-plugin (remove all openjdk-java packages or just the icedtea plugin if you have any openjdk dependent applications installed) to install sun-java enable the archive.canonical partner repository in software sources and update the software package list then you can find sun-java6-plugin in package manager.

---

### Post by Ghost_Mazal on 2010-11-17
> **gandaran said:**
>  enable the archive.canonical partner repository in software sources and update the software package list .

Already enabled. No sun java 6 plugin though

---

### Post by Ghost_Mazal on 2010-11-17
Ok got the sun java 6 (looked in wrong place)

I removed icedtea and installed sun java 6 plugin.

Still the same. Firefox freeze , and crashes with Adobe Flashplayer 10 script error
Just crashes faster now

---

### Post by SeijiSensei on 2010-11-17
I'm using the beta x64 version of Flash from Adobe's website and get the same error.  Considering that the report concerns a script problem it's either poor programming or the programmer wrote something that only works well with Windows or 32-bit Flash.  Many web developers never really test things across platforms very extensively, and 64-bit Linux is probably not a platform they are concerned about.

---

### Post by Ghost_Mazal on 2010-11-17
Guess I'll just have to live with if for 6 more days.

One more reason I wont use 64 bit again.

---

### Post by efflandt on 2010-11-17
In both 10.04 and 10.10 64-bit with earlier flashplugin-installer (32-bit flash with nswrapper), libflashplayer.so sometimes segfaulted crashing npviewer.bin in Firefox.  Although, I never really noticed when it happened (maybe flash ads) other that crash report in 10.10 beta and checking /var/log/messages in 10.04.

That site works fine in 10.10 for me (counts down seconds, minutes, etc.) with:
Firefox 3.6.12
Shockwave Flash 10.2 r161 (from flashplayer_square_p2_64bit_linux_092710.tar.gz)
GT 220 using nvidia 260.19.21 (from x-swat respositories)
Visual Effects: Normal
i5 650 3.2 GHz, 8 GB RAM

---

### Post by Irony on 2010-11-17
> **SeijiSensei said:**
> I'm using the beta x64 version of Flash from Adobe's website and get the same error.
Works fine for me with 10.04 and flash square 64 bit (right clicking also works and it zooms etc).

---

### Post by Ghost_Mazal on 2010-11-18
Thanx for the info's guys. Will give that Shockwave and square a try as well thanx

---

