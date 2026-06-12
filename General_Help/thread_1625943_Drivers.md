---
title: "Drivers"
date: 2010-11-19
forum: General Help
---

### Post by entaroadun on 2010-11-19
I have an asus 1101 ha with 2 gb of ram with Intel GMA500 gaphics module. 
I want to know what version of Ubuntu should i install on it to have graphics wireless wired and fn keys work. (not necessarily out of the box ) but i need them all to work. If you know the tweaks that work please post them here and explain how its done 
Thank you

---

### Post by cchhrriiss121212 on 2010-11-19
For the graphics:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
You don't mention what wireless chip you have so I'd recommend you just test it out with a live cd.

---

### Post by entaroadun on 2010-11-22
> **cchhrriiss121212 said:**
> For the graphics:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)
You don't mention what wireless chip you have so I'd recommend you just test it out with a live cd.The wireless works graphics works fine i just cant figure out why video playing doesn't work even if i installed the necessary codecs i only get the sound of the video

---

### Post by t4thfavor on 2010-11-22
I have an 900A, with 2GB of ram, it plays vids better than my AMD 64x2 with 4GB ram. I just use plain old Ubuntu, or xubuntu since things seemed to be slowing down as of late. All is working, including screen bright/dim, wifi/wifi button, sleep to ram.

I just actually downgraded to 512mb of ram (used it elsewhere, and saved battery) since I never was able to use more than a few hundred megs even with firefox and youtube :)

---

### Post by entaroadun on 2010-11-23
> **t4thfavor said:**
> I have an 900A, with 2GB of ram, it plays vids better than my AMD 64x2 with 4GB ram. I just use plain old Ubuntu, or xubuntu since things seemed to be slowing down as of late. All is working, including screen bright/dim, wifi/wifi button, sleep to ram.

I just actually downgraded to 512mb of ram (used it elsewhere, and saved battery) since I never was able to use more than a few hundred megs even with firefox and youtube :)very interesting i have to keep looking my 1101 ha has 2 gb ram sleep wifi dim wierd everything works im just having some problems with video i installed the codecs but it still wont play video i can only get the sound from a video file...

---

### Post by cchhrriiss121212 on 2010-11-23
> **entaroadun said:**
> The wireless works graphics works fine i just cant figure out why video playing doesn't work even if i installed the necessary codecs i only get the sound of the video
It is displayed in the link I posted, video playback is broken on all versions apart from 9.10.

---

### Post by entaroadun on 2010-11-23
> **cchhrriiss121212 said:**
> It is displayed in the link I posted, video playback is broken on all versions apart from 9.10.And i am guessing there is no way of fixing this and i need to install 9.10 in order to be able to view videos right ?

---

### Post by cchhrriiss121212 on 2010-11-23
Right, 9.10 is still supported so that gives some time to see whether it will be fixed in a newer version. I just noticed that the guide states xv playback is broken, so maybe before reinstalling try out other video outputs like X11 or GLX.
In VLC go to Tools>Preferences>Video>Output.

---

### Post by entaroadun on 2010-11-25
> **cchhrriiss121212 said:**
> Right, 9.10 is still supported so that gives some time to see whether it will be fixed in a newer version. I just noticed that the guide states xv playback is broken, so maybe before reinstalling try out other video outputs like X11 or GLX.
In VLC go to Tools>Preferences>Video>Output.i havent managed to get video playback on 10.10 but i installed 9.10 witch theoretically is supported but for some reason pulsbo does not start so i basically have no graphics and everything is moving in slow-motion. Is there a way to start pusbo driver manually ?

---

