---
title: "Radeon HD 6850 Drivers?"
date: 2011-02-01
forum: General Help
---

### Post by Cam! on 2011-02-01
I don't know what to do. When I install ATI Catalyst, choosing it gives me an error message, and when I activate proprietary drivers, my screen becomes a glitched mess.

How do I make Ubuntu 10.10 work with my ATI Radeon HD 6850?

---

### Post by khamil8686 on 2011-02-01
have you tried to install the fglrx package through your package manager or goto ati.com page and downloaded the driver for your card and installed it manually? id try installing fglrx through your package manager first since the repos have stable software, the manual install might be newer than whats in the repos and may or may not be stable but it might be able to support your card if the repos cant

---

### Post by Cam! on 2011-02-02
I installed the drivers + Catalyst from ATI.com. However, I can't access Catalyst and gives me an error message. How do I do what you stated?

---

### Post by khamil8686 on 2011-02-02
you can try going to System > Administration > Hardware Drivers and see if the manual install updated that to say that a driver was activated, then deactivate it there and try to reactivate it after a reboot at Hardware Drivers
or you can launch System > Administration > Synaptic Package Manager and search for fglrx, see if that is installed and if it is, uninstall it and reboot then go back into Synaptic and install fglrx (if it says which version of fglrx it is do a google search to see which version supports your graphics card first before choosing one to install)

also if you have troubles i just found that AMD has an unofficial wiki for people that have ati cards
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

* Also before reinstalling a graphics driver you may want to browse this thread and make sure you have your old driver completely uninstalled before reinstalling to make sure that theres no funny settings sitting around messing things up
[http://ubuntuforums.org/showthread.php?t=1056539](http://ubuntuforums.org/showthread.php?t=1056539)

---

### Post by Cam! on 2011-02-02
....So should I have the ATI.com drivers installed or uninstalled before trying the fglrx stuff?

---

### Post by khamil8686 on 2011-02-02
yes sorry that wasn't  too clear, I added that as an  after thought, first uninstall the drivers if you have any installed :)

---

### Post by Cam! on 2011-02-02
I have nothing so far. Clean slate. Do I install the ATI drivers from ATI.com, and then do fglrx, or do I just do fglrx from the start?

---

### Post by khamil8686 on 2011-02-02
from a clean slate first try to goto System> Administration > Hardware Drivers and activate the recommended driver first and reboot to see if it works

---

### Post by Cam! on 2011-02-02
You mean "Additional Drivers"? There isn't an option for Hardware Drivers. I've done that before, and when I do that, it's heavily glitchy/pixel-y to the point where it's unusable.
[[IMG]http://thumbnails40.imagebam.com/11785/4dfd12117847162.jpg[/IMG]](http://www.imagebam.com/image/4dfd12117847162)

---

### Post by khamil8686 on 2011-02-02
yes thats what i meant, i was thinking you installed the ati drivers from the ati page and then activated drivers :P ok so instead of that look for the fglrx package and install that

---

### Post by Cam! on 2011-02-02
What version of FGLRX can support the ATI Radeon HD 6850?

---

### Post by khamil8686 on 2011-02-02
11.1 is the one available from the ati website so try the highest version you can find, the one in the repo will be more stable than whats on the ati website, when i searched the packages it only showed me a fglrx package and didnt show me versions to choose from

---

### Post by Cam! on 2011-02-02
> **khamil8686 said:**
> 11.1 is the one available from the ati website so try the highest version you can find, the one in the repo will be more stable than whats on the ati website, when i searched the packages it only showed me a fglrx package and didnt show me versions to choose from

Where exactly do I find version 11.1 of FGLRX and install it?

---

### Post by khamil8686 on 2011-02-02
i thought you had found several versions of fglrx in the synaptic package manager when i said get the highest you can find :)
goto System > Administration > Synaptic Package Manger
when in there type in fglrx and hit enter and it should show you a list of packages that were found, select the fglrx package and choose to install it (right click fglrx and choose install) then hit apply and it should install fglrx for you, then reboot and see if your screen looks much nicer, you can also check by opening up a terminal and typing
```
cat /etc/X11/xorg.conf
```
and it will display your xorg.conf file, it should say Driver "fglrx" or something similar to that within that file

---

### Post by guisar on 2011-02-04
There are NO drivers which support the 6850; their website advertises support but it does not exist.. Three years ago I was all AMD/ATI. This is the last ATI card I buy and I'm sorry I bought it. ATI just doesn't care about Linux so I'll return the favor.

---

### Post by hamiltenor on 2011-02-05
> **guisar said:**
> There are NO drivers which support the 6850; their website advertises support but it does not exist.. Three years ago I was all AMD/ATI. This is the last ATI card I buy and I'm sorry I bought it. ATI just doesn't care about Linux so I'll return the favor.

Yeah, I downloaded the driver package provided by AMD, but have to see it working. Yes, AMD has released a driver for the HD6850, but 10.10 still refuses to recognise it.

Not really Ubuntu's fault, I blame AMD.

---

### Post by Flipflops4life on 2011-02-15
I dunno if this will help but here is a link to a similar thread. I got my Radeon HD 6850 running by following the directions on this page. There are also instructions on how to remove the AMD watermark.

The latest driver release screwed everything up for me though, but that might just be me.


Best of luck
[http://ubuntuforums.org/showthread.php?t=1614444&page=5](http://ubuntuforums.org/showthread.php?t=1614444&page=5)

---

### Post by machine420 on 2011-03-31
Cam i have the same problem with my radeon 6850 driver....did you find any solution to this problem? whenever i use the "additonal drivers" in system menu and activate the driver my screen goes blank. When i use the open source driver my screen also goes a total mess

---

### Post by vitotol on 2012-03-08
hello people, i going to buy that card and i wonder if the problem still persists?

the fglrx driver is not working with it?

if i have to switch to windows to use that card then i'm not going to buy it.

---

