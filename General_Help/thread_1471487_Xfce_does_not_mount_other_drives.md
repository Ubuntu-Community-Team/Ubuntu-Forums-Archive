---
title: "Xfce does not mount other drives"
date: 2010-05-03
forum: General Help
---

### Post by ubunterooster on 2010-05-03
I like the 20 second boot from press of power button with my new install, BUT I can't mount drives with xfce's thunar. I _can_ mount them with thunar but this way they still do not show up under places or on my desktop. How do I figure out how to mount them properly?

---

### Post by zvacet on 2010-05-03
From synaptic install** pysdm**.Read [this.]("http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm")

---

### Post by ubunterooster on 2010-05-03
It mounts the drives but, as with Nautilus, I can't see the mounted disks in Thunar or the xubuntu desktop.

---

### Post by ubunterooster on 2010-05-11
Side-by-side of nautilus and thunar after doing a reinstall

Thunar is on the right.

---

### Post by ubunterooster on 2010-05-12
still the same...

---

### Post by ubunterooster on 2010-05-14
Can I force xfce to use nautilus as the default file manager?

---

### Post by azertyh on 2010-05-14
> **ubunterooster said:**
> Can I force xfce to use nautilus as the default file manager?

i'm interesting of that too. i have ubuntu but installed xfce. i prefer using nautilus with gnome or xfce session.

---

### Post by JKyleOKC on 2010-05-14
> **ubunterooster said:**
> It mounts the drives but, as with Nautilus, I can't see the mounted disks in Thunar or the xubuntu desktop.What directory are you mounting the drives in? The automatic display in "places" will happen only if they are mounted in /media so if you're mounting them somewhere else that may be your problem...

---

### Post by ubunterooster on 2010-05-14
Once I mount said drives via nuatilus they do show up in /media but still not in "places"

---

### Post by ubunterooster on 2010-05-15
How many bumps is too many?

---

### Post by wilee-nilee on 2010-05-15
I have started to use xfce and xubuntu again, and had noticed this as well. You might try this other forum, I haven't joined but they will probably have an answer.
[http://forum.xfce.org/](http://forum.xfce.org/)

---

### Post by ubunterooster on 2010-05-15
So it's not just me!  I'll make a xubunterooster acct there Monday.

---

### Post by demosthenese on 2010-05-15
Drives appear in the bookmark pane - Ctrl-B, not the tree view - Ctrl-T. Your picture only shows the tree view.

Edit:
For removable drives to show on the desktop

Desktop Settings->Icons tab. Set the relevant tick box.

---

### Post by wilee-nilee on 2010-05-15
> **demosthenese said:**
> Drives appear in the bookmark pane - Ctrl-B, not the tree view - Ctrl-T. Your picture only shows the tree view.

Edit:
For removable drives to show on the desktop

Desktop Settings->Icons tab. Set the relevant tick box.

I think there is only a show or not show option, I have xubuntu removed right now, so I could be mistaken.

---

### Post by demosthenese on 2010-05-15
For drives to be shown in thunar, you definitely need to be in the bookmark view for the side pane not the tree view as shown in the picture.

It might also be necessary to have either fam or gamin installed for an existing thunar window to update when a drive is mounted. Not sure about this but worth trying. I have found gamin to be more stable - others say the opposite.

---

### Post by ubunterooster on 2010-05-15
> **demosthenese said:**
> Drives appear in the bookmark pane - Ctrl-B, not the tree view - Ctrl-T. Your picture only shows the tree view.

Edit:
For removable drives to show on the desktop

Desktop Settings->Icons tab. Set the relevant tick box.Icons are set to show on desktop for mounted media. See attachment for thunar vs nautilus in bookmark mode

---

### Post by ubunterooster on 2010-05-19
> **wilee-nilee said:**
> I have started to use xfce and xubuntu again, and had noticed this as well. You might try this other forum, I haven't joined but they will probably have an answer.
[http://forum.xfce.org/](http://forum.xfce.org/)
Still awaiting acct confirmation there so I will bump the post here

---

### Post by rectangled on 2010-09-29
I'm having a bit of trouble with this too, the ddrive mounts fine after following this post:
[http://ubuntuforums.org/showthread.php?t=178620](http://ubuntuforums.org/showthread.php?t=178620)

But the drive icon only shows up when I'm logged in as root, so this could be a permissions issue? I'm not sure how to fix it though

---

### Post by rijnsma on 2011-09-04
I saw this by accident. But beter late then never.

It is not part of Xfce, but if you don't mind some extra kde-dependency-files and an extra filemanager: install Dolphin and kdesudo.
Make an icon for Dolphin on the desktop, then: 
open the desktop entry with f.i. Leavepad and edit:

> [Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=dolphin
Comment=
Categories=Application;
**Exec=kdesudo dolphin**  ('su' maybe for not-Ubuntu-like distro's)
Icon=gdu-expander
Terminal=false
StartupNotify=false

No parameters behind dolphin.

And in the left panel of Dolphin you will see your partitions and disks. (I don't remember if this is immediatly. But sooner or later they'll show up.)

You can do everything now (even copy and paste) _over the whole system_. 

It's a shame this still is sometimes a problem in Linux after years. I can't afford not to be able to reach my disks in a decent way! I put this construction in every distro I try or use. It makes live easy. (I don't trust 'The Cloud' very much... some people put everything in it...) I had this problem years ago en eventually found this a perfect solution (for me).:)

Nautilus with rootrights (in the repo) is a little less privileged.
But maybe you like that better.

---

### Post by hhh on 2011-09-04
Sorry I didn't see this earlier. In your screenshot, you said Thunar is on the right, it's not.

I just wrote these instructions for setting Nautilus as the default a day or two ago...

[http://ubuntuforums.org/showpost.php?p=11215171&postcount=24](http://ubuntuforums.org/showpost.php?p=11215171&postcount=24)

I hope that helps.

---

