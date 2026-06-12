---
title: "flash in firefox not working"
date: 2009-10-05
forum: General Help
---

### Post by eatsubway on 2009-10-05
Sorry, if this is posted in the wrong place but...

I'm having trouble getting flash to work in firefox. Every time i go to a site which requires flash, I get a message telling me i need to download the latest version of adobe flash. Flash does work on seamonkey however.  I have spent several days trying to resolve this and it's starting to get to me.

I am running Ubuntu 9.04 on a quad core 64 bit with firefox 3.5.3 (let me know if u need more specs)

I have tried downloading flash in add/remove
   -I have "macromedia flash plugin" installed.
   -but I cannot install "adobe flash plugin 10", because 

[SIZE=1][I]                         "Adobe Flash Plugin 10 cannot be installed on your computer type (amd64). 
                          Either the application requires special hardware features or the vendor decided 
                          to not support your computer type."[/I][/SIZE]

I have tried downloading the .deb from the flash site, but i get the message

[SIZE=1][I]Adobe Flash Player plugin version 10
This package will download the Flash Player from Adobe. It is a Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use the Flash plugin. This package officially supports the following browsers:
Firefox 2.x, Firefox 3.x, SeaMonkey 1.11 [/I][/SIZE]

I have tried [this]("http://johnbokma.com/mexit/2008/11/25/64-bit-adobe-flash-ubuntu.html")
and I have already tried [this]("http://ubuntuforums.org/showthread.php?t=1259102")
and nothing seems to work

I would love it if someone could help me resolve this problem.
btw: sorry if this was already asked/answered somewhere already, feel free to post links.
thanks

---

### Post by itsbrad212 on 2009-10-05
this happened to me too. first, close all firefox windows. then open Applications>Accessories>Terminal and type this in:

```

**sudo apt-get install flashplugin-nonfree**

```

---

### Post by eatsubway on 2009-10-05
> **itsbrad212 said:**
> this happened to me too. first, close all firefox windows. then open Applications>Accessories>Terminal and type this in:

```

**sudo apt-get install flashplugin-nonfree**

```

sorry, forgot to mention that i tried that already. I just get the message...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-test phonon libkcddb4 amarok-common kdemultimedia-kio-plugins
  libqt4-webkit libloudmouth1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by foxmulder881 on 2009-10-05
If you have it working in SM then it's not a flash issue but rather a FF issue.

---

### Post by wojox on 2009-10-05
You have to follow this thread: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by itsbrad212 on 2009-10-05
yea foxmulder881 might be right this is probably a firefox issue. try searching around to find a third party plugin, or downgrade your version of firefox

---

### Post by Vaphell on 2009-10-05
my synaptic says you need only flashplugin-installer package and flashplugin-nonfree is transitional and can be removed after installing installer

**locate libflashplayer.so**
/usr/lib/flashplugin-installer/libflashplayer.so

---

### Post by eatsubway on 2009-10-05
> **Vaphell said:**
> my synaptic says you need only flashplugin-installer package and flashplugin-nonfree is transitional and can be removed after installing installer

**locate libflashplayer.so**
/usr/lib/flashplugin-installer/libflashplayer.so

what exactly are you suggesting i do with the **libflashplayer.so **file?

---

### Post by eatsubway on 2009-10-05
> **itsbrad212 said:**
> yea foxmulder881 might be right this is probably a firefox issue. try searching around to find a third party plugin, or downgrade your version of firefox

I tried downgrading to 3.0 and that still didnt fix it. Im not so sure a third party would work. Are you suggesting a different plugin to display flash rather than adobe? It seems silly that I should have to do that, but I'm up for trying anything at this point.

---

### Post by Vaphell on 2009-10-06
i don't suggest anything, installing flashplugin-installer puts flash plugin (libflashplayer.so) right there and it works here in my 9.04

where is that libflashplayer.so located in your system and does about:****plugins show it at all?

---

### Post by eatsubway on 2009-10-06
> **Vaphell said:**
> i don't suggest anything, installing flashplugin-installer puts flash plugin right there and it works here in my 9.04

where is that libflashplayer.so located in your system and does about:plugins show it at all?

well... after listening to another post i've just reinstalled firefox, so there arent any plugins currently.

the libflashplayer.so file i just put into ~/.mozilla/firefox-3.5/plugins.

also. I just installed a browser called "shiretoko" by mozilla which i have never heard of till now. and a fresh install of that, played flash videos no problem. (doesnt make sense)

---

### Post by Vaphell on 2009-10-06
shiretoko is the 3.5 version, it was not ready at the ubuntu 9.04 release so is not considered 'official' and uses codename.
clearly ~/.mozilla/firefox-3.5/plugins is the good place to put that plugin :-), but it's not system wide so if there are any other users you have to duplicate to their respective home dirs or find a proper place in system dirs

---

### Post by fergusmacdonald on 2009-10-06
Hey,

Having a similar, but not identical problem.

Flash is working for some content, but not working properly for other content.

For example, BBC iPlayer is not working (error message saying 'content not available'), banner on [http://buyakilt.com](http://buyakilt.com) shows control buttons all the time (should only show on mouseover).

I've tried uninstalling and reinstalling flash plugins and firefox, and have tried both FF 3.0 and Shiretoko 3.5 to no avail.

Running 9.04 amd64 (installed only a few days ago).

Any ideas what i can try?
Thanks.

PS:
About:plugins
 File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999 enabled

---

