---
title: "poor streaming video performance with 9.10"
date: 2010-04-19
forum: General Help
---

### Post by jensenguy on 2010-04-19
Im having some problems getting youtube videos and the like to play reasonably. Right now Im seeing pretty much every tenth frame or so if Im lucky. And half the time firefox will bring a transferring data bar up at the bottom and dim my screen. Never seen that before. 

Im on an older laptop, 32 bit - but with windows streaming videos were flawless. Also on my system at home with 8.10, and actually less recent hardware then this laptop, the videos play fine as well. As far as I know I have all the latest firefox and flash updates. 

Watching my system monitor my memory usage stays pretty low during the videos - like 240megs out of 432. But my cpu usage does go close to 100 percent. 

Any ideas? thanks

---

### Post by linden940 on 2010-04-19
do you have the most-up-to-date driver for the video card?

---

### Post by jensenguy on 2010-04-19
I dont have any video drivers installed, just however ubuntu set it up. Im having trouble finding any drivers for linux. Being a laptop Im not sure what exactly I have video wise. I know its ATI and its on board, using some of the system RAM. Anyone know of a good place to find a driver for this? This is a compaq presario 2108.

---

### Post by lovinglinux on 2010-04-19
> **jensenguy said:**
> I dont have any video drivers installed, just however ubuntu set it up. Im having trouble finding any drivers for linux. Being a laptop Im not sure what exactly I have video wise. I know its ATI and its on board, using some of the system RAM. Anyone know of a good place to find a driver for this? This is a compaq presario 2108.

Most of the time you don't need to download anything from web sites. In Linux, softwares and drivers are downloaded from a repository provided by the developer. Additionally, with a few exceptions, most of the time the drivers that come with the OS will work out-of-the-box.

So go to "System >> Administration >> Hardware Drivers" and select the one you need from the list, then click activate.

BTW, about flash performance and CPU usage, if you are on single core CPU, then most likely that you will need to upgrade it. Flash in Linux is very CPU intensive. depending on the machine it plays well, but still uses lots of CPU. For instance, I have a Core 2 Duo 2.9GHz and flash uses 40% of my CPU. 

Cleaning the CPU fan also helps. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by snowpine on 2010-04-19
Unfortunately some older ATI cards are not well supported by newer Linux distros (like Ubuntu 9.10). And Flash is a lot more CPU intensive in Linux than in Windows, which only compounds the problem. 

I recommend finding out exactly which ATI card you have (use the terminal command 'lspci' or consult your computer's manual) and using the forum Search feature at the top right for more info. There are a number of informative threads on the various ATI cards and driver options.

One thing that works well for me on my old ATI-card laptop is to download the video, then watch it from my hard drive using mplayer (or vlc or whatever video player you prefer). This gets a much better framerate than watching the same video streaming (but still not excellent). Worst case if you cannot find an ATI driver that works is to roll back to an older Ubuntu release; 8.04 will be supported through April 2011.

---

### Post by cdaringe on 2010-04-19
i am unsure of the validity of this suggestion, but you may want to quickly try using an alternate flash plugin.
there is the commercial flash plugin and the "free" plugin available in the ubuntu software repositories.  open up your synaptic package manager, search for flash plugin.  see if you can uninstall one and install the other.
realistically, will you get significantly better performance?  probably not, but its a quick shot in the dark.  may as well rule it out

---

### Post by node8472 on 2010-04-19
try some of these:
[http://lovinglinux.megabyet.net/?page_id=220#Compiz,-Xorg-and-Graphics-Tweaks-2](http://lovinglinux.megabyet.net/?page_id=220#Compiz,-Xorg-and-Graphics-Tweaks-2)

---

### Post by jensenguy on 2010-04-20
Well, Ive tried a couple of the ideas you've given me, no luck so far. My video card is a ATI Radeon mobility. Looking in synaptic it shows I have the xserver xorg ati and radeon drivers installed, but nothing will come up under Administration/ Hardware Drivers. Only a driver for my wireless card shows up. 

Do I need to have drivers other than what was installed with ubuntu? And shouldn't I be able to see them in the hardware drivers screen?

---

### Post by alindi on 2010-04-20
i have also noticed this since last week....any help

---

### Post by snowpine on 2010-04-20
> **jensenguy said:**
> Well, Ive tried a couple of the ideas you've given me, no luck so far.

Did you try downloading the video first then watching it from your hard drive, like I suggested in post #5?

Did you find out which specific card you have, then use the forum Search feature to find more information? (Hint: [ATI has manufactured many different cards]("http://en.wikipedia.org/wiki/Radeon") known as Radeon Mobility; you need to know which specific one you have, usually a 4-digit number, use the terminal command 'lspci -nn | grep VGA' to find out.)

Also, the Ubuntu help pages are a good resource: 
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

