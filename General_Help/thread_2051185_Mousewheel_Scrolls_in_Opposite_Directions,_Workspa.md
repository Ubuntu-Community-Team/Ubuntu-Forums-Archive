---
title: "Mousewheel Scrolls in Opposite Directions, Workspace Switching Doesn't Work"
date: 2012-09-01
forum: General Help
---

### Post by ohnonot on 2012-09-01
Hello everybody!

I'm getting better at creating precise thread titles ;-) - not much to add to this.

so, when i scroll down, it scrolls up and when i scroll up it scrolls down. happens in firefox as well as in file manager (thunar or pcmanfm).

my installation is originally xubuntu but i did a lot of tweaking. for a long time i thought this is an openbox thing, but now i booted into the default xubuntu session with xfwm4 as window manager, and it's the same. 
[openbox has a feature for workspace switching by scrolling on the desktop background, and there it gets even worse: it switches quickly  to the other workspace and back to the first (i have only two).]

i have now freaking clue what's happening here...
:confused:
thankful for any help!!!

---

### Post by 2F4U on 2012-09-01
In Xubuntu, did you check Settings Manager -> Mouse and Touchpad -> Reverse scroll direction?

---

### Post by ohnonot on 2012-09-04
> **2F4U said:**
> In Xubuntu, did you check Settings Manager -> Mouse and Touchpad -> Reverse scroll direction?it was UNchecked, so i checked it. works in xubuntu session.
but with openbox i'm not using the setting manager anymore - strangely, checking it worked for a few seconds, then it unchecked itself again????

---

### Post by ohnonot on 2012-09-11
problem persists.
further exploration: raising number of workspaces to 4: workspace switching by way of scrolling on the desktop switches 2 workspaces at a time. so from 1 to 3 (although i see 2 flickering for a moment) and from 3 back to 1.

logging into the default xubuntu session, everything works nicely except the mouse wheel scrolls in the wrong direction. i can fix it by checking "reverse scroll direction" in the xfce4-settingsmanager->mouse.

maybe this is not openbox specific - i was thinking that maybe i have 2 mouse drivers running at the same time?

any help, ideas, explanation is appreciated!

thanks.

ps: the mouse is part of a logitech wireless optical desktop mk250, that's wireless keyboard and mouse sharing one usb receiver. touchpad (this is an old laptop) is disabled in the bios.

---

### Post by ohnonot on 2012-09-11
2 SOLUTIONS!

1.) (the openbox bit) here:
[https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)
"If you have a problem changing virtual desktops with the mouse wheel skipping over desktops, edit ~/.config/openbox/rc.xml. Move the *mouse binds with...* actions "DesktopPrevious" and "DesktopNext" from context *Desktop* to the context *Root*. Note that you may need to create a definition for the *Root* context as well"


2.) scrolling in opposite directions:
[http://maketecheasier.com/reverse-mouse-scrolling-direction-in-ubuntu](http://maketecheasier.com/reverse-mouse-scrolling-direction-in-ubuntu)
In my home folder there was a file called .Xmodmap with the following content:
pointer = 1 2 3 5 4 6 7 8 9 10 11 12- i simply deleted it.
i think exchanging the numbers 5 and 4 would have had the same effect.



- still i wonder, why did all this happen in the first place???

---

