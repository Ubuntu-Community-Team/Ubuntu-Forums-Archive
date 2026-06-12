---
title: "Broken Xorg? Very sudden break."
date: 2010-10-29
forum: General Help
---

### Post by Wolvenreign on 2010-10-29
Hey all.

I was recently watching an avi file, when suddenly, my tower (the computer) got really, really noisy. That's pretty normal when I'm on my Windows side, but very unusual for Ubuntu Linux. I knew something was in the wind then and there.

So I exit my Dragon Player to discover that ! gasp ! KDE is down, replaced with the default wallpaper for GNOME, and no bars anywhere. I reset the system only to find that it refuses to boot into either KDE or GNOME. Having been in something similar to this situation before, I decide that Xorg.conf must be broken somehow. In an effort to get to the GUI where I can safely edit it, I try reinstalling KDE and GNOME, which both failed.

So I try installing xdm...which results in only being able to access the login screen for XFCE. Whenever I try to log in using the correct credentials, it simply refreshes the log-in screen.

So my questions are as follows...

1. Is this, indeed, the sign of a broken Xorg.conf, or a broken Xserver in general? Or is there something larger that was changed?

2. How do I fix this? (I've already tried using Ubuntu 10.10 64 in rescue mode, but I can't seem to change anything in the system itself.)

3. Is this possibly a result of upgrading straight from 10.04? Is it possible that having both KDE and GNOME contributed to this?


Thank you very much for your time.

---

### Post by squaregoldfish on 2010-10-29
Your best bet is to look at the X log - /var/log/Xorg.0.log - see if there's any errors listed there.

Steve.

---

### Post by Wolvenreign on 2010-12-03
```
(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.674] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  3 14:17:03 2010
```

This was the only error I could find in Xorg.0.log.

---

