---
title: "xscreensaver missing fonts"
date: 2012-07-24
forum: General Help
---

### Post by squaregoldfish on 2012-07-24
From a clean install of 12.04 from the 64-bit alternate CD, I added xscreensaver and all its demos. Unfortunately it reports missing fonts for some of them. For example:

```

starwars: font -*-utopia-bold-r-normal-*-*-720-*-*-*-*-iso8859-1 does not exist, using -*-helvetica-bold-r-normal-*-180-*
starwars: font -*-helvetica-bold-r-normal-*-180-* does not exist, using fixed
starwars: unable to load font "-*-utopia-bold-r-normal-*-*-720-*-*-*-*-iso8859-1", using "-*-helvetica-medium-r-normal-*-240-*"
starwars: unable to load font "-*-helvetica-medium-r-normal-*-240-*", using "-*-helvetica-medium-r-normal-*-180-*"
starwars: unable to load font "-*-helvetica-medium-r-normal-*-180-*", using "fixed"

```

I've installed the texlive recommended fonts package which claims to contian utopia, but it hasn't made any difference - the fonts aren't even viewable in xfontsel.

Any ideas what needs to be done to get these fonts properly registered and working in xscreesaver?

Steve.

---

### Post by Toz on 2012-07-24
Does:
```
sudo fc-cache -v -f
```
...get them registered properly?

---

### Post by squaregoldfish on 2012-07-25
Nope. Still the same message (ran as sudo and as me).

---

### Post by Toz on 2012-07-25
Have a look at the bug report: [https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/222367]("https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/222367").

---

### Post by squaregoldfish on 2012-07-27
I think that's a different issue - xscreensaver has always had issues with UTF8 encodings, but accented Latin characters have been fine.

The problem here is that none of the fonts that xscreensaver expects to use are installed in Ubuntu and the lettering therefore looks horrible. I can't figure out where to get them from.

The fact that I've installed utopia fonts and yet xfontsel can't see them is indicative of a more fundamental issue that I haven't been able to figure out as yet.

Steve.

---

### Post by Toz on 2012-07-27
> **squaregoldfish said:**
> The fact that I've installed utopia fonts and yet xfontsel can't see them is indicative of a more fundamental issue that I haven't been able to figure out as yet.


Agreed. I've just finished trying to install this font with no luck on precise and some luck on quantal.

First, the font is hard-coded into the executable: [http://xscreensaver.sourcearchive.com/documentation/4.21/starwars_8c-source.html]("http://xscreensaver.sourcearchive.com/documentation/4.21/starwars_8c-source.html"). However, the font is no longer part of any official package in the repositories.

You "should" be able to add this font to the existing system. I found the font here: [http://set.ufpa.br/repositorio/pool/main/s/set-root/opt/ltsp/i386/usr/X11R6/lib/X11/fonts/100dpi/]("http://set.ufpa.br/repositorio/pool/main/s/set-root/opt/ltsp/i386/usr/X11R6/lib/X11/fonts/100dpi/"), downloaded it and added it to /usr/share/fonts/X11/100dpi. Then did the regular stuff:
```
sudo mkfontdir
sudo mkfontscale
sudo xset fp rehash
```

On precise, I get the following error when running xset:
> xset:  bad font path element (#1), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax


On quantal, xset succeeds (shows up with xlsfonts), but when I try to run the program:
```

$ /usr/lib/xscreensaver/starwars -window
starwars: stale texture font error: invalid enum

```

I was, however, able to specify another font for the program to use:
```
/usr/lib/xscreensaver/starwars -font "-*-impact-bold-r-*-*-*-720-*-*-*-*-iso8859-1"
```
...and that worked perfectly.

---

### Post by squaregoldfish on 2012-07-27
So that should mean you can edit your .xscreensaver file and adjust the command line for the relevant savers to make them use a sensible font. I haven't tried it yet to confirm though.

Steve.

---

### Post by Toz on 2012-07-27
> **squaregoldfish said:**
> So that should mean you can edit your .xscreensaver file and adjust the command line for the relevant savers to make them use a sensible font. I haven't tried it yet to confirm though.

Steve.
Yes.

```
 GL: 				starwars -root -font "-*-impact-bold-r-*-*-*-720-*-*-*-*-iso8859-1"		    \n\
```
...works for me.

---

