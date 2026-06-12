---
title: "Changes To Audio Have Rendered My Mixer Apps Useless"
date: 2010-07-04
forum: General Help
---

### Post by Mark76 on 2010-07-04
Anyone know how to fix it?

[ATTACH]162428[/ATTACH]

---

### Post by ajgreeny on 2010-07-04
You don't say which mixer apps, and your txt file is not helpful, so I've no idea!

Just use alsamixer instead, if it does what you want.

---

### Post by Mark76 on 2010-07-04
I mean the volume control plugin for my panel. It's now useless thanks to something that's been done to python-alsaaudio.

Everytime I try to add it to the panel it tells me that an integer is required, and I've no idea what that means or why it's never told me that before.

---

### Post by ajgreeny on 2010-07-05
You need the **indicator applet** in your panel for the older style volume control, but you also need access to the **pulseaudio volume control** from the Sound & Video menus to get the degree of control that you probably need.

---

### Post by Mark76 on 2010-07-05
Perhaps the developers would care to tell me why default is no longer a valid mixer option in Ubuntu.

Except that you can't, can you.

For the record Gnome is not my primanry desktop environment.

---

### Post by Mark76 on 2010-07-05
I've made these two screenshots to illustrate the problem.

I'm sorry they're not more informative, but you've screwed up python-alsaaudio so badly that I can't even save the bug report that's generated when the Volume panel applet fails to be created.

[ATTACH]162506[/ATTACH] [ATTACH]162507[/ATTACH]

---

### Post by ajgreeny on 2010-07-05
Sorry, but I still don't really understand what your problem is.

Gnome 2.30 has made a lot of changes to the desktop, and ubuntu has taken them along with the gnome desktop for its Lucid version.  This is why the old volume control applet is now gone and the new one is just a part of the indicator applet, and not a separate item as it used to be.

Similarly pulseaudio is the newest, and now, I think the best, sound server there is.  It is a lot more complicated than previous sound systems, but it does allow you to, for example, set different volume levels in each application, rather than a blanket single overall volume for everything.

Keep trying it and playing with it, and you may find it is better than you think at the moment.  Yes, it is different but that does not mean that it is bad.

---

### Post by Mark76 on 2010-07-05
I found a version of Volume that has a patch to fix whatever was wrong in python-alsaaudio.

---

