---
title: "Unexpected new font behavior ( partial changes; wrong size; etc. )."
date: 2009-12-03
forum: General Help
---

### Post by endBc on 2009-12-03
[[IMG]http://img31.imageshack.us/img31/5117/200912031526471280x1024.th.png[/IMG]](http://img31.imageshack.us/i/200912031526471280x1024.png/)

Why the font changes are visible only in 1 window and the font/size of other windows increases ( from Sans 10 Regular to Sans 12 Regular ) ?

---

### Post by quixote on 2009-12-04
Did you reboot after making the changes?  Also, which change are you trying to get, Sans 10 to 12, or from Sans 12 to 10?  Where did you make the changes?  "Appearance Preferences" Fonts?  There's a whole series of different window types there, and changing it in one will not change the others.

---

### Post by endBc on 2009-12-04
Ok, here's an explanation to what I tried to do and what happened:

```
Current font: Sans 10 Regular
Changed to Gotham Nights 12 Regular
[COLOR=Red]Font changed in lxappearance from Sans 10 Regular to Gotham Nights 12 Regular
Font changed in everything else from Sans 10 Regular to Sans 12 Regular[/COLOR]

```Did a few restarts but nothing changed. Any ideas ?

---

### Post by quixote on 2009-12-04
(I'm not sure what you mean by the window "lxappearance.")

I take it the Gotham Nights font is a special one you downloaded?  I don't see it on my system so I'm guessing it's not standard.  Given that the change you want is appearing in one window, "lxappearance", that implies the font is available to the system.  Without that, my guess would have been that maybe the font cache wasn't updated.  It looks like the Sans 12 is the system's best guess for what you want once it can't find Gotham.  But then why does it find it once?  I'm not sure. :(

This is the standard procedure: After you download a font and put it in /usr/share/fonts/truetype or one of the other subdirectories where it might belong, then you update the fontcache: ```
sudo fc-cache -f -v
```

Hope any of this helps.

---

### Post by endBc on 2009-12-05
Updated. Still nothing. lxappearace is pretty much the same as Appearance settings for Gnome, except, this one is for LXDE.
Gotham Nights is a custom font downloaded from urbanfonts.com and I'm sure it's 100% working ( tested on OpenOffice.org, Photoshop and font viewer ).

Something is wrong but I can't figure out what .. Everything works unless I add a custom font.

---

### Post by quixote on 2009-12-05
Yes, if OO and other programs find the font, then it's definitely available.  I didn't realize you were working with LXDE.  It's not something I know anything about.  My guess would be that there's something in that desktop manager that has a quirk.  Somebody who knows more about LXDE needs to jump in! :)

---

