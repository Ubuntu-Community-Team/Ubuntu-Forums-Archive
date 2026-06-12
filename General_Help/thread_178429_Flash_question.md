---
title: "Flash question"
date: 2006-05-17
forum: General Help
---

### Post by drfox on 2006-05-17
There is a REALLY hilarious flash site at [www.shaveeverywhere.com](www.shaveeverywhere.com) (it's a Norelco site, and I don't have any relationship with Norelco) that I can't see on my Linux machine using FF 1.5.01 and Flash 7.06 (I think).

Is there something I can do to update my Flash or use another plug-in to view this site?

Larry

---

### Post by olsonar on 2006-05-17
nope. flash 8 isn't available for linux yet.

---

### Post by Fac51 on 2006-05-17
i have an issue with flash, but it's not because i need flash 8.... i'm not seeing text

is there a fix for this at all??

---

### Post by Fac51 on 2006-05-24
FIXED
thanks to a person who goes by linportal i have fixed this issue

linportal wrote:
```
OK, if you have doublechecked everything and still have that same problem I would suggest the following:

- install x-ttcidfont-conf package
- install msttcorefonts package
- install freefont package
- install ttf-bitstream-vera package
- install ttf-xfree86-nonfree package

That should get you a fine collection of truetype fonts to start. Now, go edit your /usr/X11R6/lib/X11/fs/config (deliberately using that long path to ascertain file is in place) and make sure you have /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/ path listed in the catalogue line. Even better, copy this (it's proven to work) and put it in the config file:

catalogue = /usr/share/fonts/X11/misc/,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/,
/usr/share/fonts/X11/Type1/,
/usr/share/fonts/X11/100dpi/,
/usr/share/fonts/X11/75dpi/

It should all be on one line (broken here just for presentation purposes) and without spaces between paths. Restart xfs, restart firefox. Now, do you see any difference, do you see text in flash now?
```

if you're on Debian or Ubuntu, make sure the packages that are listed in the first portion of this article. You will more than likely need to create some needed symlinks, but according to the information given, it shouldn't be too hard to figure out.

---

