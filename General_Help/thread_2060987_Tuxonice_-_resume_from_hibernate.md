---
title: "Tuxonice - resume from hibernate"
date: 2012-09-21
forum: General Help
---

### Post by LGI-MP on 2012-09-21
I've been using tuxonice successfully for the past several months.  However, the last two days I have not been able to resume under a specific set of circumstances (under which I previously had no problem).  Yesterday I just had a black screen (perhaps with a mouse cursor) - I attempted to just type my password and see if it would log in, but that didn't work. When I reset, it said that my display driver had crashed.  Today when resuming I was able to log in to the desktop but unity didn't seem to work (the windows had no decoration which included the close, minimize, max/restore buttons; there was no sidebar panel with apps; nor to my memory was there a top system bar), so I did a shutdown -r.

The circumstances which were present both times were hibernating while connected to an external monitor (broadcasting only to the ext monitor and not using the internal monitor), keyboard and mouse (with laptop lid closed) and network cable. I resumed with only the mouse connected (and possibly, but not likely connected with the network cable as well), so am using the built in keyboard and monitor.

When I resumed today, in addition to the basic issues with lack of window decoration and dash/launcher, the display was only using the left 80% of the widescreen panel, indicating that it didn't flip resolution back to internal monitor standard.  I was also missing a gnome-panel bottom toolbar, but that may have been off the viewable region of my desktop if the resolution was not reset.

Incidentally, when hibernating while connected to the external monitor, it has ALWAYS had the tuxonice hibernation off-center, indicating that tuxonice is trying to use, rather than the external monitor's rez, the laptop built-in resolution for that process (even though it's being broadcast to the monitor via an analogue connection).


Kernel: 3.2.0-30-generic-tuxonice #48~ppa1-Ubuntu SMP Thu Sep 6 23:56:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

computer model: HP pavilion dm4-1165dx (with intel-based internal graphics)

---

### Post by LGI-MP on 2012-09-26
I found the following script and am attempting to use it.  Unfortunately I haven't replicated the exact conditions that lead to the lockups, so I'm not 100% sure it works (there might be something added to specifically locate graphics drivers, as this was primarily written for USB device issues):

[http://chriseiffel.com/everything-linux/how-i-got-suspend-and-hibernate-working-in-linux-ubuntu-11-04-mint-11/](http://chriseiffel.com/everything-linux/how-i-got-suspend-and-hibernate-working-in-linux-ubuntu-11-04-mint-11/)

I just thought I'd put that out there in case anyone else comes across THIS thread and has the same issue as me.

---

