---
title: "Screensaver/Sleep? Outta Control!"
date: 2010-06-12
forum: General Help
---

### Post by bigsmitty64 on 2010-06-12
Hi all, 
 I'm running Lucid 32 bit desktop

I have my screen saver options off. (activate screen saver when computer is idle for_____ is UNCHECKED,
 I have no power options set. (this is a desktop so I have it all set to stay on, all the time. Put computer to sleep when inactive for: NEVER
Put display to sleep when inactive for:NEVER
Yet, when I leave it for more than 5 or so minutes it goes to a blank screen. I don't see what I'm missing here. Someone will know, I just know it. :) 
Thanks in advance,
Smitty

---

### Post by bigsmitty64 on 2010-06-12
bumpage

---

### Post by bigsmitty64 on 2010-06-13
Surely someone has the answer :)
I've noticed the power light on the monitor turns red when this happens. So its def not the screensaver, it's going to sleep, but why?

---

### Post by bigsmitty64 on 2010-06-21
Still an issue here, anyone?

---

### Post by MooPi on 2010-06-21
I've never questioned this option as it only takes a mouse click to get the screen back up , but every install I have does this regardless of the power setup. Not a solution but you seemed peeved that no one responded.

---

### Post by bigsmitty64 on 2010-06-21
No No, not peeved in the least! I just figured its time for a bump. My last install  (karmic) didn't have this issue. Its not really a **HUGE** problem just an annoyance. Thats why I waited a week :) I figure there has to be a way to turn this off right? Thanks for the response!

---

### Post by tim042849 on 2010-06-21
I'm having a similar problem.
See my posting at
[http://ubuntuforums.org/showthread.php?t=1514279](http://ubuntuforums.org/showthread.php?t=1514279)
these problems are just **awful!**
Can somebody please help? 
It is very disappointing to see these issues unresolved.
tim

---

### Post by bigsmitty64 on 2010-06-21
It is a pain in the butt huh? I've learned though to have patience here on the forums because it's a busy place and someone ALWAYS helps in the end.

---

### Post by tim042849 on 2010-06-21
> **bigsmitty64 said:**
> It is a pain in the butt huh? I've learned though to have patience here on the forums because it's a busy place and someone ALWAYS helps in the end.
I hope someone helps, because my posting is buried several pages back by now. 
Linuxquestions is as busy, I believe, but I always get answers.
(about my slack install).
thanks
tim

---

### Post by bigsmitty64 on 2010-06-22
The official "dam close to 24 hour" bump! :)

---

### Post by tim042849 on 2010-06-22
> **bigsmitty64 said:**
> The official "dam close to 24 hour" bump! :)
I just installed the **recommended** nvidia proprietory driver.
I'll see what happens. BTW: I have three machines here with lucid.
It is only my wife's compaq that has this problem.
cheers

---

### Post by bigsmitty64 on 2010-06-24
**Wikipedia:**
*Loneliness* is often compared to feeling  empty, unwanted, [B]...  :)
[/B]

---

### Post by tim042849 on 2010-06-24
> **bigsmitty64 said:**
> **Wikipedia:**
*Loneliness* is often compared to feeling  empty, unwanted, [B]...  :)
[/B]
I know the feeling. I've posted again, no help but some sympathetic
remarks. Have you tried Launchpad? I'm going to soon.
cheers

---

### Post by hhh on 2010-06-24
[http://ubuntuforums.org/showthread.php?p=9505367#post9505367](http://ubuntuforums.org/showthread.php?p=9505367#post9505367)

---

### Post by bigsmitty64 on 2010-06-24
> **hhh said:**
> [http://ubuntuforums.org/showthread.php?p=9505367#post9505367](http://ubuntuforums.org/showthread.php?p=9505367#post9505367)

```
An often suggested fix is to add the following to the end of you  xorg.conf file:

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection
```


My xorg.conf is **way** different than that ?


```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

---

### Post by hhh on 2010-06-25
Yah, but my link says to add the ServerFlags stuff to the end of your file, and add the DPMS option in your "Monitor" section before the line "EndSection. So add the following to the bottom of your file (assuming you don't already have a section named "Monitor" in your file...

```
Section "Monitor"
Option "DPMS" "off"
EndSection

Section "ServerFlags"
    Option         "BlankTime" "0"
    Option         "StandbyTime" "0"
    Option         "SuspendTime" "0"
    Option         "OffTime" "0"
EndSection
```

Don't know if that will work, but worth a shot.

---

