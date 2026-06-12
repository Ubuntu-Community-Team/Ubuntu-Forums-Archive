---
title: "Ambiance Theme"
date: 2010-03-05
forum: General Help
---

### Post by ShroudedCloud on 2010-03-05
Alright, so I downloaded both the mono-icon theme and the light-themes packages, both are the most recent versions. For some reason though, the metacity part of it works fine (the title bar has the icons all in the proper place/order), but for some reason the GTK part doesn't work, EXCEPT the scroll bar which appears properly themed. Everything else about the theming does not seem to work at all.

I've checked, and all the dependent files and suck are up-to-date, etc. I've tried getting the .deb directly (found here: [https://launchpad.net/ubuntu/lucid/i386/light-themes/0.1.5.4](https://launchpad.net/ubuntu/lucid/i386/light-themes/0.1.5.4) )and a version that was specifically made as a backport to Karmic (found here: [https://launchpad.net/~kalon33/+archive/ppa](https://launchpad.net/~kalon33/+archive/ppa) ). Can anyone help?

I've included an image so you can see what it is I'm trying to describe.

EDIT: I should also mention that the panels are also not being themed.

EDIT 2: New development, it appears I have inadvertently stumbled closer to what the issue is, but I am still very unsure:

I was testing something as I asked another person what they thought and went to run gedit as root when this happened
```

$ sudo gedit "new file"
[sudo] password for [user]: 
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:80: error: unexpected identifier `arrowstyle', expected character `}'
```

So, it's something to do with whatever is utilizing that gtkrc file itself, but my knowledge ends there. I hope that this information will be useful to you all.

---

### Post by Intrepid Ibex on 2010-03-05
Well I dunno if it's gonna help at all, but did you try relogging?

---

### Post by ShroudedCloud on 2010-03-05
Yes, I did restart and re-login several times in attempt to get this to work. The only change that did make was to makes the metacity icons move to their proper place because before the restart, they'd been in the wrong order/place.

---

### Post by ShroudedCloud on 2010-03-05
I guess I should mention that in the file, at the line in question, it goes something like this: ```
78:text[INSENSITIVE] = shade (0.6, @base_color)
79:
80:	engine "murrine" {
81:		arrowstyle         = 1
``` 
And goes on from there (not missing the closing bracket as far as I can tell as the engine bracket is a subset of a larger part.

---

### Post by ShroudedCloud on 2010-03-06
Alright, after some assistance it was found that if the 'arrowstyle' and 'comboboxstyle' lines that are found near after line 80 are commented out, the issue is fixed.

---

