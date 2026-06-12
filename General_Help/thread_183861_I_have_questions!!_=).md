---
title: "I have questions!! =)"
date: 2006-05-28
forum: General Help
---

### Post by Profusion on 2006-05-28
Hi everyone!

I have Dapper installed and love it! I do however have a few tiny issues I have been trying to iron out but seem to have difficulty getting the right source or answer.

Currently applied to my system.
[B]
Desktop PC[/B]

XGL - working
Compiz - working
Bumps - working except flash stopped working after awhile
TV - Was using TVtime, stopped working after XGL and Compiz install


**Notebook**

Dell D810
XGL - working
Compiz - working
Bumps - working even flash sound
Wireless - detecting in networking as Lan1 but using every App in the add/remove 
for wireless seem to detect access points but I cannot connect with applied info.


**So summary..**

[COLOR="Purple"]Wireless cannot connect but is detected
Flash sound stopped working
TV time stopped working after XGL Compiz install[/COLOR]

[COLOR="Purple"]How can I get these to work? [/COLOR]

Also a few nit pick if someone knows a quick answer.

1. When opening up quick launch apps with XGL/ Compiz installed it has a slow rendering of the animation box before the app opens up. Is there a way to speed that up?



Thanks to everyone for past help much appreciated!

---

### Post by Profusion on 2006-05-28
[QUOTE=Profusion]Hi everyone!

I have Dapper installed and love it! I do however have a few tiny issues I have been trying to iron out but seem to have difficulty getting the right source or answer.

Currently applied to my system.
[B]
Desktop PC[/B]

XGL - working
Compiz - working
Bumps - working except flash stopped working after awhile
TV - Was using TVtime, stopped working after XGL and Compiz install


**Notebook**

Dell D810
XGL - working
Compiz - working
Bumps - working even flash sound
Wireless - detecting in networking as Lan1 but using every App in the add/remove 
for wireless seem to detect access points but I cannot connect with applied info.


**So summary..**

[COLOR="Purple"]Wireless cannot connect but is detected
Flash sound stopped working
TV time stopped working after XGL Compiz install[/COLOR]

[COLOR="Purple"]How can I get these to work? [/COLOR]

Also a few nit pick if someone knows a quick answer.

1. When opening up quick launch apps with XGL/ Compiz installed it has a slow rendering of the animation box before the app opens up. Is there a way to speed that up?



Thanks to everyone for past help much appreciated![/QUOTE]

Anyone?

---

### Post by henriquemaia on 2006-05-28
[quote=Profusion]Anyone?[/quote]

Probably this isn't the answer you need, but I would recommend you not to use XGL/compiz while it is not stable. There are always uknown side effects of using it, like your "[COLOR=Purple] TV time stopped working after XGL Compiz install". [COLOR=Black]

I really love XGL/Compiz, but I'm not using for this reason. Good luck, anyway.

[/COLOR][/COLOR]

---

### Post by apollyonis on 2006-05-28
I don't know if this will help, but it may be a good starting point for the tvtime issue : 
[XGL info]("http://www.ubuntuforums.org/showthread.php?t=98456&highlight=xgl")

---

### Post by CyberCam on 2006-05-28
[QUOTE=henriquemaia]Probably this isn't the answer you need, but I would recommend you not to use XGL/compiz while it is not stable. There are always uknown side effects of using it, like your "[COLOR=Purple] TV time stopped working after XGL Compiz install". [COLOR=Black]

I really love XGL/Compiz, but I'm not using for this reason. Good luck, anyway.

[/COLOR][/COLOR][/QUOTE]

I would have to agree with henriquemaia, I too stop using XGL/Compiz for the same reason. Plus it kinda got old very quickly with me. Eyecandy is good and all but stability with all my apps is much more valuble to me.

When XGL/Compiz becomes stable, then, and only then will I use it again! :-|

---

### Post by Profusion on 2006-05-28
[QUOTE=CyberCam]I would have to agree with henriquemaia, I too stop using XGL/Compiz for the same reason. Plus it kinda got old very quickly with me. Eyecandy is good and all but stability with all my apps is much more valuble to me.

When XGL/Compiz becomes stable, then, and only then will I use it again! :-|[/QUOTE]


Ohh I thought after watching that Novell XGL video it was ready for public. I guess like you said its not ready (stable) OK well that about sums it up them. I guess ill use it until im board of it or untill there are some fixes out there for it =) thanks again guys!

---

### Post by RAOF on 2006-05-28
[QUOTE=Profusion]Ohh I thought after watching that Novell XGL video it was ready for public. I guess like you said its not ready (stable) OK well that about sums it up them. I guess ill use it until im board of it or untill there are some fixes out there for it =) thanks again guys![/QUOTE]
Nope!  It's missing a bunch of important stuff - dual monitor support has only just been introduced, XVideo acceleration is a bit iffy (mythtv crashes XGL without fail), overlay support (which, from memory, is what TVTime uses) is also iffy :)

You can get around all of these problems by running a second, non-XGL X server to run the things that don't work in, but it **is** just a work-around.

---

### Post by Profusion on 2006-05-29
[QUOTE=RAOF]Nope!  It's missing a bunch of important stuff - dual monitor support has only just been introduced, XVideo acceleration is a bit iffy (mythtv crashes XGL without fail), overlay support (which, from memory, is what TVTime uses) is also iffy :)

You can get around all of these problems by running a second, non-XGL X server to run the things that don't work in, but it **is** just a work-around.[/QUOTE]

Oh really how do I do that?

---

### Post by RAOF on 2006-05-30
[QUOTE=Profusion]Oh really how do I do that?[/QUOTE]
Um... I'm not sure what the best way is, but you can run multiple virtual-terminal X servers by editing the gdm.conf-custom, like with XGL.

Where you have
```
[servers]
0=XGL
```
You can add ```
[servers]
0=XGL
1=Standard
```
and have a standard X server & an XGL server at the same time.

A better solution might be the one from the "run games in XGL fast" thread, but I haven't tried that.

---

### Post by pedwards on 2006-06-01
reguarding your wireless woes, do you have broadcom chipset / and if so do you have your bcmwl5 files?

---

### Post by cblanquer on 2006-08-26
Regarding tvtime, this solution should work (but ttvtime runs at the price of high CPU consumption).
Check in thread:
[http://www.ubuntuforums.org/showthread.php?t=209843&highlight=compiz+tvtime](http://www.ubuntuforums.org/showthread.php?t=209843&highlight=compiz+tvtime)

---

