---
title: "Equivalent download manager?"
date: 2009-10-11
forum: General Help
---

### Post by raunchyrex on 2009-10-11
I recently migrated for windows and was wondering if there are any equivalents to 
[LIST=1]
[*]Internet Download Manager
[*]Adobe Flash
[*]Bandwidth Monitor(Any software to check the amount of data transferred)
[/LIST]

Also, in windows I used to have a resolution of 1184 x 789 but in Ubuntu 9.04 the maximum I'm allowed is 1024 x 768
Any help on this?

Regards,
Rex

---

### Post by ikt on 2009-10-11
> **raunchyrex said:**
> I recently migrated for windows and was wondering if there are any equivalents to 
[LIST=1]
[*]Internet Download Manager
[*]Adobe Flash
[*]Bandwidth Monitor(Any software to check the amount of data transferred)
[/LIST]

Regards,
Rex

1. kget
2. adobe flash
3. bmon / system > admin > system monitor

Head to Applications > add/remove applications to install the above.

---

### Post by durand on 2009-10-11
[D4X]("apt://d4x") is a pretty good downloader.

---

### Post by raunchyrex on 2009-10-11
> **ikt said:**
> 1. kget
2. adobe flash
3. bmon / system > admin > system monitor

Head to Applications > add/remove applications to install the above.
Hello mate, I appreciate your replying but mind being a little precise with 

```
bmon / system > admin > system monitor
```

> **ikt said:**
> 2. adobe flash
Is there a linux version?

---

### Post by XCan on 2009-10-11
2. Yes there is a linux version. The 32-bit can be easily installed through the repos, the 64 bit I recommend you to download the "alpha (which is very stable tbh)" from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) . 

3. I believe the system monitor can tell you how much you've transferred during the active session, you can also view this by typing ```
 ifconfig 
``` However, I prefer vnstat which gives a history of the transfers in days, weeks, months etc.

---

### Post by raunchyrex on 2009-10-11
'ifconfig' works great! But I installed 'vnstat' none the less. Now I can't figure how to launch it :(

Btw, is it possible to make things a little glossy? Everything seems way too bland for my taste! :D (Can't help it, WINDOWS spoiled me)

---

### Post by Arup on 2009-10-11
Multiget is equivalent of Widnows DM, flash is there for Ubuntu from Adobe, for bandwidth monitoring I use gkrellm which is in the repos, not only does it monitor bandwidth but it does much more than that.

---

### Post by durand on 2009-10-11
> **raunchyrex said:**
> 'ifconfig' works great! But I installed 'vnstat' none the less. Now I can't figure how to launch it :(

Btw, is it possible to make things a little glossy? Everything seems way too bland for my taste! :D (Can't help it, WINDOWS spoiled me)

vnstat is really good! It is however commandline only. Open a terminal and type in vnstat --longhelp. That should help you. If you only want to get the bandwidth for the day, you can just use the system monitor: System > Administration > System Monitor from the main menu.

Oh and for glossiness, try changing your themes. Go to gnome-look.org and pick out a few icon and gtk themes. You can install them by opening up Appearance preferences (System > Preference > Appearance) and dragging and dropping the files. You could also install emerald themes if you use compiz.

---

