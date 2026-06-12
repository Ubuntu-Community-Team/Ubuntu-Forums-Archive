---
title: "Installing Gnome Shell messed with my main system"
date: 2010-02-03
forum: General Help
---

### Post by jcapinc on 2010-02-03
Hey, real quick here:

:KS**This is my problem:**
[LIST]
[*]I installed gnome-shell, it worked, I was impressed, I stopped using it
[*]When I stop using it, I found that it changed my system, for the worse
[/LIST]

:KS**These are the changes it made to my system:**
[LIST=1]
[*]Startup services do not run, I have to run programs manually
[*]I cannot lock my screen, either by hotkey or the normal menu applet
[*]Totem no longer prevents the screen from going blank while playing
[/LIST]

Its like some sort of system service is not starting, I'm sure there are other symptoms that I have forgotten.

All of these problems are livable, but inconvenient.  I should have known better than to mess with my system, but I wish I knew how to reverse it.  Naturally I uninstalled gnome-shell but it did nothing.

:confused: Any Ideas?  Thanks in advance :)

---

### Post by jcapinc on 2010-02-05
**An update:**

The problem is worse than I origianally thought.  It turns out no events that no gksu events work.  I cannot install anything or mount any hard drives.

Please help!! this is a real headache.

Thanks

---

### Post by Roasted on 2010-02-05
Did you reboot at all?

---

### Post by jcapinc on 2010-02-05
I have found the main problem, it turns out the only issue is that my startup applications do not run, all of my other issues stem from that.

So does anyone know what gets called where to run the startup applications found in the startup applications preferences?

AND:

> **Roasted said:**
> Did you reboot at all?

Yes, I had restarted several times before, and I just restarted several times just now.

---

### Post by afrodeity on 2010-02-07
Thanks for warning us. I have problem compiling gnome-shell on Karmic [http://paste.ubuntu.com/370829/](http://paste.ubuntu.com/370829/) mesa-utils *is* installed.

---

