---
title: "PCManFM - No Desktop Tab"
date: 2010-11-02
forum: General Help
---

### Post by Lucradia on 2010-11-02
There's no desktop tab in ubuntu's PCManFM, how do I get it to be the desktop manager in this case? Also, pcmanfm -d just opens pcmanfm, doesn't start it in daemon mode.

---

### Post by kerry_s on 2010-11-02
right click pcmanfm desktop.

when was the last time you used pcmanfm? there have been many changes.

do-> pcmanfm --help
in terminal.

---

### Post by Lucradia on 2010-11-02
> **kerry_s said:**
> right click pcmanfm desktop.

when was the last time you used pcmanfm? there have been many changes.

do-> pcmanfm --help
in terminal.

Several months ago, is when I used it, thanks for the help. I didn't have pcmanfm running as desktop, so I can't right-click its desktop.

---

### Post by hantms on 2011-10-17
Strange that this is set to 'SOLVED' then there is no solution. 

I had the same issue, running LXDE on Ubuntu Oneiric, and accidentally getting stuck with a very yuckie Openbox desktop-context menu.   There are instruction s on the internet that this can be changed in the Desktop tab in the pcmanfm file manager in Edit->Preferences. However there is no Desktop tab.

The solution is to open a terminal window and launch pcmanfm with the --desktop-pref option, and now the Desktop Preferences box appears. Click the 'Advanced' tab, then tick off the box for 'Show menus provided by window managers when the desktop is clicked'.

Note that after doing this you can easily get back to the desktop preferences panel again just by right clicking the desktop and selecting Desktop Preferences.

So now the [SOLVED] is accurate.  ;)

(If anyone wonders why you would use LXDE with Ubuntu at all, it's because I run it on a free-tier Amazon EC2 instance, and with heavy desktop environments you run into the CPU cap all the time.  The Midori browser is a blessing in this respect over Firefox as well. )

---

