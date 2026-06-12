---
title: "Firefox crashing after update"
date: 2012-02-04
forum: General Help
---

### Post by G Luv on 2012-02-04
Firefox crashes repeatedly on startup.

Ubuntu 10.10. 64-bit. Firefox 10.0. Immediately after a Firefox upgrade, it started crashing upon opening, going straight to the "We're Sorry..." bug report screen.

$ firefox -P     does the same thing.

I know I have flash-plungin-installer installed, but can't tell you much else because, well, I can't even get firefox open, of course.

Can't say I'm super ubuntu-savvy, so feel free to be very explicit about the next steps.

---

### Post by dragonfly41 on 2012-02-04
Try command
[B]
firefox -safe-mode[/B]

---

### Post by G Luv on 2012-02-04
> **dragonfly41 said:**
> Try command
[B]
firefox -safe-mode[/B]

Thanks. Unfortunately, it still crashes.

---

### Post by dragonfly41 on 2012-02-04
More suggestions here ..

[https://wiki.ubuntu.com/MozillaTeam/Bugs](https://wiki.ubuntu.com/MozillaTeam/Bugs)

and here (click on the replies)

[http://linux.bigresource.com/Ubuntu-Firefox-continually-crashing-with-10-04-solve-this--ouWSkbnkq.html](http://linux.bigresource.com/Ubuntu-Firefox-continually-crashing-with-10-04-solve-this--ouWSkbnkq.html)



see one suggestion #5 posted here ..

[http://ubuntuforums.org/showthread.php?t=1390198](http://ubuntuforums.org/showthread.php?t=1390198)

> 
This is possibly a problem with the hidden folder ~/.mozilla in your  home, so try renaming that. [COLOR=Red] Don't remove it [/COLOR]as it contains all your  bookmarks, and your history which is why that was still in place, plus  cookies, etc etc.


but backup ~/.mozilla before trying this !!   And close firefox first.   
You can restore your firefox profile .. folder by folder .. from your backup.

---

### Post by G Luv on 2012-02-04
Thanks.

Can anyone tell me how to revert to the previous version?

---

### Post by dragonfly41 on 2012-02-04
Read here ..

[http://ubuntuforums.org/showthread.php?t=1920305](http://ubuntuforums.org/showthread.php?t=1920305)

not recommended to use an older copy of firefox.

You can always install Opera as an interim browser until firefox problem is fixed.

---

### Post by krishnamohan on 2012-02-05
I had the same problem after an update today...Disabling a particular add-on, Image lookup, solved the problem....

---

### Post by lovinglinux on 2012-02-07
If it crashes when you launch it with *firefox -P*, then you need to reinstall, because neither a clean profile or safe mode will make any difference.

try this:

```
sudo apt-get install --reinstall firefox
```

---

### Post by krishnamohan on 2012-02-08
I am not sure that is right...

For me , firefox -P also caused a crash.....

But it ran in safe mode after disabling all the add-ons...

---

### Post by lovinglinux on 2012-02-08
> **krishnamohan said:**
> I am not sure that is right...

For me , firefox -P also caused a crash.....

But it ran in safe mode after disabling all the add-ons...


If it ran in safe mode, then run it again, but select the option to disable all add-ons and restart. Then re-enable each add-on, one-by-one and restart, to find which one is causing the problem.

---

