---
title: "Just installed the upgrade Ubuntu Lucid and display does not turn off"
date: 2010-05-04
forum: General Help
---

### Post by berlinbrown on 2010-05-04
I just did the upgrade and I want to turn off the display after 30 minutes.  I check that selection but the display does not turn off after 30 minutes.  It is still on.

I enabled this setting through the power management.


The screen saver is on, go to blank display but the monitor does not turn off.

On Windows, dual boot on the same machine, the monitor does display off.

I don't know if this is part of the problem or not, but when I go to "System -> Preferences", there are two different "Screensaver" options.

---

### Post by Jingo on 2010-05-16
I'm having the same problem.

Anything new. I would like my laptop to dpms off the screen after 10 min on ac and 5 min on battery.

---

### Post by dsauxier on 2010-07-14
I'm having the same issue on one computer - it was a fresh install of Mythbuntu 10.04.

My Ubuntu 10.04 desktop (my main pc) does NOT have this issue, it was an upgrade from several previous releases, not a fresh install.

---

### Post by BuckNaked on 2010-08-10
I got this problem too. KDE seems to turn off display correctly, but it's too memory/cpu intensive for me. I'm using now XFCE (XUbuntu). But sadly XFCE display off doesn't seem to work either. 

This : ```
xset -display :0.0 dpms force off
``` works just fine, though. I don't think it's a problem with my hardware since on 9.10 it worked fine.

If I can't get a good solution i guess i'll just make Xubuntu use that command instead of screensaver...

Anybody a fix?

---

