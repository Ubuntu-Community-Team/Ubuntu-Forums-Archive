---
title: "youtube videos and site lagging."
date: 2009-11-01
forum: General Help
---

### Post by sudoer541 on 2009-11-01
Anyone experiencing this? videos on youtube and even the whole site lags on 9.10. I mean OMG like seriously thats a bit annoying. btw I am using firefox 3.5.4 etc. 
any suggestions fellow ubuntians?  



:popcorn:

---

### Post by lovinglinux on 2009-11-01
Do you have the latest driver for you video card enabled?

What do you get after this command:

```
glxinfo | grep -i direct
```

See the Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by hoppipolla on 2009-11-01
yeah a combination of the best codec and the best drivers fixes most things like this :)

---

### Post by overdrank on 2009-11-01
From a support thread of the op
> ATI radeon 9250 
I believe to be the issue. :)

---

### Post by sudoer541 on 2009-11-01
> **lovinglinux said:**
> Do you have the latest driver for you video card enabled?

What do you get after this command:

```
glxinfo | grep -i direct
```See the Flash Optimization section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

I get 


**direct rendering: Yes**

---

### Post by sudoer541 on 2009-11-01
> **overdrank said:**
> From a support thread of the op

I believe to be the issue. :)

well if thats the issue, then how can you explain that the lagging and the resolution problem **[COLOR=DarkRed]did not [/COLOR]**occur in previous versions of ubuntu? 

merci!

---

### Post by Exodist on 2009-11-01
> **sudoer541 said:**
> Anyone experiencing this? videos on youtube and even the whole site lags on 9.10. I mean OMG like seriously thats a bit annoying. btw I am using firefox 3.5.4 etc. 
any suggestions fellow ubuntians?  



:popcorn:

Yes its CPU throttling. Add the scalling apt to the task bar or just turn off CoolNQuite off in the BIOS.
Even with generic 2D drives for your card it would still work great.  
Not sure why everyone on this forum tells everyone its the freaking video card. /sigh

---

### Post by sudoer541 on 2009-11-01
> **Exodist said:**
> Yes its CPU throttling. Add the scalling apt to the task bar or just turn off CoolNQuite off in the BIOS.
Even with generic 2D drives for your card it would still work great.  
Not sure why everyone on this forum tells everyone its the freaking video card. /sigh


cool and quite mode was already disabled on BIOS, and I just enabled it to see if it makes a difference. if it doesint then I am going to disable it again. 

btw if it helps here are my pc specs:

```
AMD athlon 64 @ 2200GHZ
Video card: ATI radeon 9250 with 128MB ram
1GB ram 
2 separate hard disks for ubuntu and windows xp
```



edit
with cool and quite enabled it does not make a difference, videos and sites with flash and java content lag aggressively.

---

### Post by sudoer541 on 2009-11-02
I believe that there gotta be a reason for why previous version of ubuntu could run perfectly on my hardware that hasint changed since I started using ubuntu. I never had the resolution and the video (flash and java) lagging problem and now it occurs and there is no fix for it. I have been using the ati open driver I believe since I started suing ubuntu. is there a way I can revert to the old open driver?

---

### Post by NoaHall on 2009-11-02
64 bit ubuntu?

---

### Post by Exodist on 2009-11-02
> **sudoer541 said:**
> cool and quite mode was already disabled on BIOS, and I just enabled it to see if it makes a difference. if it doesint then I am going to disable it again. 

btw if it helps here are my pc specs:

```
AMD athlon 64 @ 2200GHZ
Video card: ATI radeon 9250 with 128MB ram
1GB ram 
2 separate hard disks for ubuntu and windows xp
```

edit
with cool and quite enabled it does not make a difference, videos and sites with flash and java content lag aggressively.

This is troubeling for me since I have had almost the same setup before without any issues. But you did mention turning on CaQ made it worse as it should. This points me to wonder if your system is already running hot? Other then that it may be the RAM. 1GB may be pushing it. Check how much ram you are using by typing $free at the CLI. This will give you a true tell of how much RAM your system is using and if its having to pipe so much data around and that is causing the lag.

Let me know.

---

### Post by sudoer541 on 2009-11-02
> **NoaHall said:**
> 64 bit ubuntu?

32 bit

---

### Post by sudoer541 on 2009-11-02
> **Exodist said:**
> This is troubeling for me since I have had almost the same setup before without any issues. But you did mention turning on CaQ made it worse as it should. This points me to wonder if your system is already running hot? Other then that it may be the RAM. 1GB may be pushing it. Check how much ram you are using by typing $free at the CLI. This will give you a true tell of how much RAM your system is using and if its having to pipe so much data around and that is causing the lag.

Let me know.


output from free:



```
  total       used       free     shared    buffers     cached
Mem:       1025796     614512     411284          0      59428     301448
-/+ buffers/cache:     253636     772160
Swap:            0          0          0

```

---

### Post by sudoer541 on 2009-11-02
One more thing! On youtube and grooveshark I see lots of buffering every 2 seconds on firefox. Its still lagging and everything.

---

### Post by NoaHall on 2009-11-02
Then it's probably your internet connection. Youtube is known for being slow.

---

### Post by sudoer541 on 2009-11-02
> **NoaHall said:**
> Then it's probably your internet connection. Youtube is known for being slow.
I understand that youtube is slow from time to time but I talking about any site with flash video. this happens only in ubuntu but not windows. 
When I download something from the internet with ubuntu everything is fine. Only flash video gives me problems. Or anything that is java and flash related. once again, I never had this problem on previous version of Ubuntu.

---

### Post by sudoer541 on 2009-11-02
I need someone to explain this to me. Why did previous versions of ubuntu worked great with my computer with old video card and now I have major problems with viewing flash videos that are lagging and I cant go to the desired screen resolution that I had on previous version of ubuntu?

---

### Post by sudoer541 on 2009-11-02
can anyone explain this?

---

### Post by sudoer541 on 2009-11-03
:popcorn:

---

### Post by cariboo on 2009-11-03
If you really want help with your problem, you should be asking them in a help forum instead of in the Cafe, I would suggest starting a thread in the general help section.

---

### Post by CarpKing on 2009-11-03
As stated, this thread probably belongs elsewhere, but I might be able to help you anyway, as I had similar problems when I first installed Karmic.   

The ATI drivers in Karmic default to EXA for accelleration, wheras they used to default to XAA.  I'm not sure when the change took place, but I kind of think it was XAA in Jaunty.  I have been specifying EXA for longer.  The other change is that Karmic does not have an xorg.conf by default.  

When I have used EXA, flash videos are often laggy unless I specify certain options in my xorg.conf.  Currently it is as follows (if you edit yours it will be blank, but any text you add to it will be used the same as before).  

```
Section "Device"
	Identifier	"Configured Video Device"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "AccelDFS" "true"
	Option "ColorTiling" "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I hope this helps you.

---

### Post by Bunnybugs on 2009-11-03
I&#472;e experienced the same problems on 64-bit...

that one doesn really work pretty... but after finding the good java and flash player it just stopped...

getting Sun Java was hard... but worth it... and maybe you should install the right driver for your videocard.... it just lags without it, like in windows (not that bad, but it works better with the correct driver)

---

### Post by sudoer541 on 2009-11-03
> **CarpKing said:**
> As stated, this thread probably belongs elsewhere, but I might be able to help you anyway, as I had similar problems when I first installed Karmic.   

The ATI drivers in Karmic default to EXA for accelleration, wheras they used to default to XAA.  I'm not sure when the change took place, but I kind of think it was XAA in Jaunty.  I have been specifying EXA for longer.  The other change is that Karmic does not have an xorg.conf by default.  

When I have used EXA, flash videos are often laggy unless I specify certain options in my xorg.conf.  Currently it is as follows (if you edit yours it will be blank, but any text you add to it will be used the same as before).  

```
Section "Device"
    Identifier    "Configured Video Device"
    Option "EnablePageFlip" "true"
    Option "AccelMethod" "EXA"
    Option "AccelDFS" "true"
    Option "ColorTiling" "on"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```I hope this helps you.

can you please explain how can I find and edit the file you listed?

---

### Post by CarpKing on 2009-11-04
> **sudoer541 said:**
> can you please explain how can I find and edit the file you listed?

In a terminal:

```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by sudoer541 on 2009-11-17
video still lags but I think it improved a bit. any more ideas?

---

### Post by ArtzP on 2009-11-18
I just find out the problem (at least my flash lag problem) - and it could work with yours too. After fresh installation ubuntu 9.10 the flash was working- after restart it wont . I think this was ,because I installed some codecs (_totem compatible codecs_) together with mp3 codecs etc...

My solution is - **open firefox addons**- there you find **plugins **-
 **1.** _**disaple windows mediaplayer plugin (Totem)**_ [B]
2. disaple VLC multimedia plugin (Totem)[/B]. 
I disapled both and now it is the flash working. Perhaps one is enough. I hope it works with your computers too.

---

### Post by sudoer541 on 2009-11-18
> **ArtzP said:**
> I just find out the problem (at least my flash lag problem) - and it could work with yours too. After fresh installation ubuntu 9.10 the flash was working- after restart it wont . I think this was ,because I installed some codecs (_totem compatible codecs_) together with mp3 codecs etc...

My solution is - **open firefox addons**- there you find **plugins **-
 **1.** _**disaple windows mediaplayer plugin (Totem)**_ [B]
2. disaple VLC multimedia plugin (Totem)[/B]. 
I disapled both and now it is the flash working. Perhaps one is enough. I hope it works with your computers too.

ill give it a try. but I also go to other video streaming sites that might use the totem and the vlc plugin. if I disable those plugins and install media connect plugin from mozilla will it video sites work normally?

---

### Post by ArtzP on 2009-11-18
At first I saw improvement, but with high resolution flash videos lagging started again.
In youtube this kind of tool works [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771) . Pretty useful, but only working in youtube - but excelent performance.

---

### Post by sudoer541 on 2009-11-18
> **NoaHall said:**
> 64 bit ubuntu?


32 bit

---

### Post by ArtzP on 2009-11-20
After installing KDE 4.3 desktop (i don't know does it matter) and typing terminal: _**$ ****metacity --replace**_         
 (for both gnome and KDE) my videos quit lagging. Someone wiser could explaine is it possible? For my computer it worked. 
PS! I also disabled desktop visual effects (if they work- flash do not work)

---

### Post by stonebit on 2009-11-21
Delete all the flash plugins you have installed.
Download flash from adobe (there is a 64 bit version too - [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html) ) and copy it directly into your browser's plugin folder, then restart your browser.

Adobe's official garbage player is better than the reverse engineered flash plugins out there.

---

### Post by WorLord on 2009-11-24
> **CarpKing said:**
> When I have used EXA, flash videos are often laggy unless I specify certain options in my xorg.conf.  Currently it is as follows (if you edit yours it will be blank, but any text you add to it will be used the same as before).  

```
Section "Device"
	Identifier	"Configured Video Device"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "AccelDFS" "true"
	Option "ColorTiling" "on"
EndSection

```

I hope this helps you.

BINGO.  That worked great.

IBM Thinkpad T42p, ATI FireGL T2 (128M ram)

Extra option that helped even more: 
```

        Option "AGPSize"    "128"

```

:-)

---

