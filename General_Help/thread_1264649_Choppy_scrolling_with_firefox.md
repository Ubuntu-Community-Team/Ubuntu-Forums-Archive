---
title: "Choppy scrolling with firefox"
date: 2009-09-12
forum: General Help
---

### Post by withinspace on 2009-09-12
I am using Ubuntu 9.04 and firefox 3.5.4. The scrolling is very slow and choppy with firefox. (scrolling is fine with anything else) I have a Radeon 2600 video card if that helps.  Any ideas how to make my scrolling better?

---

### Post by mike555 on 2009-09-12
You should get the firefox ad-0n "  smooth wheel " .

---

### Post by Ratscallion on 2009-09-12
In Edit -> Preferences there's an option of Smooth Scrolling and Auto scrolling.. Disable Auto, if it's enabled, and put Smooth to what it is not (ie, if it's ticked, un tick it and vice versa)

---

### Post by jefromi on 2009-10-31
I just upgraded to xubuntu 9.10, and seem to have the same problem. To be precise: the content gets redrawn top-to-bottom (scroll down) or bottom-to top (scroll up) over about a quarter of a second instead of instantly. This isn't really a scrolling problem; it presents whenever the browser pane is redrawn, for example when one of those "pop-up blocked" or "remember password?" prompt-bars slides in from the top. (And of course scrolling settings have no effect)

I also notice that moving windows is now choppy - very low fps, and can see a black rectangle beneath where the window was the previous frame. Resizing windows was already choppy in 9.04; this seems to have been fixed in some places but not in others. Wonder if there's a generic issue in common? I have a Radeon 4850...


Edit:

I shut down to leave home, came back a while later and booted, and problems are all gone. Ooooooookay then.

---

### Post by yanom on 2009-11-05
1) I have the same problem

2)

> In Edit -> Preferences there's an option of Smooth Scrolling and Auto scrolling.. Disable Auto, if it's enabled, and put Smooth to what it is not (ie, if it's ticked, un tick it and vice versa)

That didn't work

3) I have the same problem in **all gtk applications** where there's a scroll bar

---

### Post by NoVista on 2009-11-06
Autoscroll has nothing to do with it.
Setting Smooth Scrolling either way doesn't help either, although one setting is somewhat better than another.

I too have developed  this problem after upgrading to 9.10.
Not on all pages though. Most Yahoo pages have the problem here.
Actually, I didn't develop it .. Firefox did :frown:

---

### Post by kooboo on 2009-11-08
Anyone found any solution?
Most "big" pages (lots of words, etc.) cause this issue for me.

Btw - I used to have similar problem under WinXP before I installed any graphic drivers. But this didn't help here.
Also - I didn't upgrade to 9.10. I have fresh system.

---

### Post by wojox on 2009-11-08
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by benj1 on 2009-11-08
for any of you with ATI cards
i found the problem was fixed by changing 

Option "AccelMethod" "EXA"
to
Option "AccelMethod" "XAA"

in /etc/X11/xorg.conf

so it should look something like

Section "Device"
 Identifier "Configured Video Device"
 Option "RenderAccel" "on"
 Option "AccelMethod" "XAA"
 Option "AGPMode" "4"
EndSection

---

### Post by kooboo on 2009-11-13
> **wojox said:**
> [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

The whole thread doesn't even contain a single word "autoscroll", "auto scroll", "autoscrolling" not to mention any solution to the issue.

Also - not an ATI card, so problem still exists.

---

### Post by solnyshok on 2009-11-18
Do you have compiz enabled? I found that it severely affects scrolling smootheness on my rig. (Both ATI and Intel graphics). So most of the time I use metacity :(

---

### Post by Andreas1 on 2009-11-18
the whole thing is most likely not a firefox issue and turning on smooth scrolling will even make it worse. i would say it is an xorg issue, unfortunately i cannot help any further because what [fixed]("http://ubuntuforums.org/showthread.php?t=1130582") this for me was only for the intel drivers (which were a disaster in jaunty).
disabling compiz always helps, of course.

---

### Post by NoVista on 2009-11-20
> for any of you with ATI cards
i found the problem was fixed by changing

Option "AccelMethod" "EXA"
to
Option "AccelMethod" "XAA"

in /etc/X11/xorg.conf

so it should look something like

Section "Device"
Identifier "Configured Video Device"
Option "RenderAccel" "on"
Option "AccelMethod" "XAA"
Option "AGPMode" "4"
EndSectionThanks Benj1, that worked.
Odd, I don't think I've used those settings since Gutsy.
I didn't even have the options listed, I added them.

---

### Post by hunterkasy on 2009-12-13
I have installed ubuntu, xubuntu on let say around 6 machines all 9.10 fully updated and every machine, no matter how old or new, slow or fast the machine is, firefox is choppy when scrolling pages, I just told people to live with it, and get over it.  but it would be nice to have it (working) normal

---

### Post by kford on 2010-02-02
```
Option        "AccelMethod" "XAA"
```

Adding this to my xorg.conf file worked for me also.  Otherwise, Firefox was a painful experience.  I'm running an Intel machine with ATI graphics.

---

