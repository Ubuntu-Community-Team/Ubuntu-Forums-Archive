---
title: "cool xfce menu in gnome?"
date: 2009-08-18
forum: General Help
---

### Post by treehouse on 2009-08-18
You know that cool menu you get in xfce and openbox when you right-click the desktop that gives you applications menues and stuff? I wanna use that on my Gnome desktop instead of the normal one. How do I do that?

---

### Post by treehouse on 2009-08-18
bump 2 hours later. I'm really hoping someone can give me some clues.

---

### Post by y-lee on 2009-08-18
> **treehouse said:**
> bump 2 hours later. I'm really hoping someone can give me some clues.

hmm never tried it, but i did find this thread : [XFCE in right click menu in  gnome]("http://ubuntuforums.org/showthread.php?t=628296")

---

### Post by Anzan on 2009-08-18
While the root menu on right click is standard in most Window Managers unfortunately neither KDE nor GNOME allow this. 

So if I use them I run apps with the run dialogue (ALT+F2) or from a terminal.

Having a (customized) root menu wherever the cursor happens to be instead of swinging the cursor around and pointing at cartoons and clicking takes way too long.

---

### Post by bodhi.zazen on 2009-08-18
> **treehouse said:**
> You know that cool menu you get in xfce and openbox when you right-click the desktop that gives you applications menues and stuff? I wanna use that on my Gnome desktop instead of the normal one. How do I do that?

To be honest, that is the reason I prefer XFCE. In addition, of the three, IMO, XFCE does a better job with multiple monitors (ie setting one background image per monitor).

---

### Post by treehouse on 2009-08-18
So I'm trying to use fluxbox as the window manager while maintaining as much of my current Gnome settings as possible. I tried the advice from [the fluxbox wiki](http://fluxbox-wiki.org/index.php?title=Faqs#Can_I_use_fluxbox_as_the_window_manager_in_GNOME) and when I enter 'gnome-session-remove metacity' I get an error: 'bash: gnome-session-remove: command not found'. What am I doing wrong?

---

### Post by bodhi.zazen on 2009-08-18
Personally I just run Fluxbox without the gnome stuff. You can run a differnt panel if you like (there are several to choose from).

I think it is easier to run openbox + gnome or LXDE.

Try ```
fluxbox --replace
``` although somehow that may not work.

The problem is that the wiki you are looking at is not accurate in terms of the version of Ubutnu you are using.

You can try these two links :

[http://ubuntuforums.org/showthread.php?t=490376](http://ubuntuforums.org/showthread.php?t=490376)

[https://help.ubuntu.com/community/ReplaceMetacityWithOpenbox](https://help.ubuntu.com/community/ReplaceMetacityWithOpenbox)

The second one is openbox and for what you are doing I think openbox will work better then fluxbox.

To generate a menu, use menumaker (I like that one) or for Fluxbox :

[marchfluxmenu - Google Code]("http://code.google.com/p/marchfluxmenu/")

---

### Post by treehouse on 2009-08-18
I got it going now (I liked openbox more than fluxbox), and my desktop looks pretty sweet. Thanks guys.

Here's what I did in case anyone is looking to do the same thing and looks up this thread in their search (I'm on Intrepid Ibex):

I installed openbox (or fluxbox) and it's configuration dealy through apt-get
```

apt-get install openbox openbox obconf

```
then went into 'System>Preferences>Sessions' and edited the value for 'Window Manager', changing it from 'gnome-wm' to 'openbox'. You could probably also change the environmental variable 'WINDOW_MANAGER' to be openbox but I did it this way because it seemed easier.

After restarting X, I found that Nautilus was still making the right-click menu, so I turned off desktop drawing.
```

gconf-editor

```
then change the value of /apps/nautilus/preferences/show_desktop to false.

Since Nautilus isn't drawing the desktop now, anything that I put in my ~/Desktop folder doesn't appear there anymore. I'm still not sure how to make that work with Openbox.

Edit: I just noticed I did exactly what was in that helpfile that you linked Bodhi, except I bypassed the gnome-wm script.

---

### Post by bodhi.zazen on 2009-08-19
Glad you got it working. Flux/Openbox are both nice.

---

