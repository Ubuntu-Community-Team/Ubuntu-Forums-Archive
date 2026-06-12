---
title: "ATI HD 3300 issues."
date: 2010-11-08
forum: General Help
---

### Post by gewone on 2010-11-08
So, I have always installed Ubuntu on old to ancient machines, for the most part being server use. Now today I decided to try it on a fairly descent desktop machine, for the very first time. Phenom II 945 (AM3) 3GHz, 4GB DDR3, etc. The graphic chipset is HD3300, on a [fairly new] [ASUS M4A78T-E]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131366") motherboard.

Installation was a success. Everything seemed to work great out of the box. My 24" LCD monitor and my 32" LCD television set showed a clone Full-HD (1920x1080) resolution, displaying the exact same.

```
gewone@robotnix:~$ lspci -nn|grep 0300
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3300 Graphics [1002:9614]
```

I even tried launching a BluRay rip á MKV without having installed ATI's proprietary drivers. Worked fine. No obvious rendering issues or anything like that. Wonderful. Now, I thought to myself, if it works this well with no actual 3rd party drivers, it must be real blast with those FGLRX drivers. The hardware hint icon was already in tray, so I clicked it and quickly installed the drivers. I then rebooted my machine.

Now comes the weirdness. At GNOME logon screen, picture was sort of distorted. It's hard to explain, but it was like there was missing pixels here and there, and they would gradually start coming back. I managed to login. The desktop locked a bit distorted too, eg. the 'Indicator Applet Session' in the top menu bar, it was distorted, sort of '½ x duplicated', or what to call it, so if my name is 'Gewielena Sienow' then it showed 'Gewiel' and then harshly went into another 'shadow' of the same first characters of the name. Weird. Tried rebooting a couple of times, the wack logon screen was present each and every time.

I finally gave up and removed the proprietary drivers. Anyways, I must admit I'm a bit of a luck-seeker. It would be really awesome to get the actual ATI drivers up and kicking, when everything else works so darn nice. It's not like with some ancient laptop I installed Ubuntu on, that without proprietary drivers, I was forced to live with 'minimal' visual effects. Oh no, I can do all three levels, even though I don't notice any different between 'Normal' and 'Extra', except that it feels like the Extra setting is lagging somewhat more.

Awergh. Anyways. I would be very thankful for any advice that you experienced guys out there could give me. I'm running Ubuntu 10.10 (maverick), just so you know. All recent updates is made, etc. So, anything with *'xorg.conf'* perhaps? Funny thing btw, since I removed the proprietary drivers and kick 'as is', there is not even a xorg.conf file inside *'/etc/X11/'*. Really funny.


[I]Ty in adv~
G.
[/I]

---

