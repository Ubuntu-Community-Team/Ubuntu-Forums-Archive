---
title: "My system time changes automatically."
date: 2011-02-27
forum: General Help
---

### Post by Lagunatic on 2011-02-27
Hey,

My system time on Ubuntu 10.10 keeps changing by itself. It now says 12:43PM when it is actually 7:43PM. I have tried manually changing it three times but it always changes itself back to another random time. And it doesn't just do it when I reboot, it just does it randomly when I'm logged in.

Is there any way to fix this?

Thanks,
Jack

---

### Post by applejuicekiss on 2011-03-26
me too.  it is maddening. i moved to a different time zone and now can't get it to stay on the new time.  tried setting a location, and it still changed back.

i haven't yet bothered to restart and go into the cmos setup to change it.  i imagine that would work...

even so, when you set the time in gnome, it should stick.

any help will is appreciated.

---

### Post by gmargo on 2011-03-26
> **applejuicekiss said:**
> i moved to a different time zone and now can't get it to stay on the new  time.  tried setting a location, and it still changed back.To set the time zone in Gnome, use the menu item System -> Administration -> Time and Date.  Then click on the not-so-obvious icon in the center of the bottom line of the window, where it says "Click to make changes".  Note that you must click on the icon to the left of the text, not the text itself.  Then you will be prompted for your password.  After you authenticate, you'll be able to use the pull-down menu to choose your time zone.

Alternatively, to set the time zone from the command line, run
```

sudo dpkg-reconfigure tzdata

```and navigate the menus to find your time zone.

---

### Post by gmargo on 2011-03-26
> **Lagunatic said:**
> My system time on Ubuntu 10.10 keeps changing by itself. It now says 12:43PM when it is actually 7:43PM. 
Probably your system is configured to assume that your hardware clock is in UTC instead of local time.  Check your **/etc/default/rcS** file and toggle the value of "UTC=yes" to "UTC=no" (or vice versa), and then reboot.

---

