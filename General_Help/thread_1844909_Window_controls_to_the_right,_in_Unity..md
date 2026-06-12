---
title: "Window controls to the right, in Unity."
date: 2011-09-15
forum: General Help
---

### Post by melrokz on 2011-09-15
I'm running Ubuntu 11.04 and would like to know how to move the window controls to the right in Unity. In Gnome, we use gconf-editor, but that does not seem to work in Unity.

Any solutions please?

---

### Post by MG&amp;TL on 2011-09-16
Not possible, AFAIK. As Unity matures, there will be more configuration tools, but currently, aside from editing source and recompiling, I don't see how you would do it.

---

### Post by cryptotheslow on 2011-09-16
I'm fairly sure one or two of the appearance themes put the buttons to the right - certainly did when I ran up a LiveCD of 11.04.

If I get a minute, I'll run it up again and see which it was :)

---

### Post by Grenage on 2011-09-16
> **melrokz said:**
> I'm running Ubuntu 11.04 and would like to know how to move the window controls to the right in Unity. In Gnome, we use gconf-editor, but that does not seem to work in Unity.

Any solutions please?

gconf-editor should still work; Ubuntu uses Gnome, Unity is just a compiz plugin.

Open gconf-editor - Alt+F2 and typing gconf-editorz will do it.
From there, it's in apps, Metacity, General.
'Button layout field', change the value to:

menu:maximize,minimize,close

---

### Post by Frogs Hair on 2011-09-16
Ubuntu Tweak  Works well for this and it has many other settings also .. [http://blog.ubuntu-tweak.com/downloads](http://blog.ubuntu-tweak.com/downloads)

---

### Post by cryptotheslow on 2011-09-16
OK...

Just ran up the 11.04 LiveCD. And yep, as I remembered these Themes move the window controls to the right:

Clear looks
Dust Sand
High Contrast Inverse
New Wave


You can change theme by going to System Settings > Appearance

I presume it's the same on an installed version and not just a quirk of the LiveCD :)

---

### Post by LMP900 on 2011-09-16
> **cryptotheslow said:**
> OK...

Just ran up the 11.04 LiveCD. And yep, as I remembered these Themes move the window controls to the right:

Clear looks
Dust Sand
High Contrast Inverse
New Wave


You can change theme by going to System Settings > Appearance

I presume it's the same on an installed version and not just a quirk of the LiveCD :)

Where do the controls go when maximized? Back to the left?

---

### Post by cryptotheslow on 2011-09-16
Oops - good point. I hadn't played around with it enough (just messing with it on LiveCD to see if I can live with Unity or no).

With the righty-button themes the behaviour is a little inconsistent.

e.g.
Control Centre and LibreOffice Writer the window controls hop up onto the top pane on the left. Weirdly the "Close Document" X on Writer stays all the way over on the right within the app - but it does that on the lefty-button themes too.

Firefox - it depends. Hit the Maximise window control and they hop up onto the left of the top pane as above. Hit F11 to go full screen instead and they stay on the right, but change style on the top bar that auto-hides.

All a bit strange - to me at least as I use the New Wave theme on 10.04 and the buttons stay consistently right as they stay within the app context of course.

I have a feeling I'll be moving to Xubuntu. That's a while off though as I'm staying with 10.04 until it goes EOL. Things will certainly have been polished with Unity by then so I'll revisit it at the time.

Only reason I find it hard to adopt lefty-buttons is that I'm forced to use WinXP for work and often have the work laptop and my own 10.04 PC running at the same time....  switching between the two with lefty-buttons just drives me nuts as I'm always going the wrong way for window controls lol.

So yeh - changing Theme is not the answer in 11.04, ignore me :D

---

### Post by wildmanne39 on 2011-09-16
Hi, Frogs Hair is correct it changes it with just a click and works great.
Thank you

---

### Post by wildmanne39 on 2011-09-16
Hi, also you can get rid of the global menu at the top and put the buttons on the window that should take care of the maximized issue.
Thank you

---

### Post by cryptotheslow on 2011-09-16
From what I read you just need to remove the indicator-appmenu package. Not sure if that is just the app menus rather than the window buttons though as I haven't tried it.

It is one of the other things that bugs me about Unity as I always run with a lot of small windows (big screen) and having to mouse to the top of the screen to hit a menu is cumbersome.

As I said - I'm just playing around with 11.04 on and off so proceed with caution :D

---

### Post by wildmanne39 on 2011-09-16
Hi, here is a link to disable or remove the app menu so the buttons will be on your windows and not the menu.
[http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html)
Thank you

---

### Post by cryptotheslow on 2011-09-16
Have you confirmed it works to bring both the window controls as well as the menus into the app context? Even when maximised?

I have to admit the more I mess with this stuff, the more I realise I am unsure about what falls under the control of the desktop environment, the window manager and the unity shell wrapped on top. Is there an antagonistic crossover of functionality between Gnome+Compiz+Unity? If so we seem to be breaking modularity for the sake of providing some slick desktop bling here.

---

### Post by wildmanne39 on 2011-09-16
Hi, no I have not personally tried what I mentioned I do not mind the buttons on the app menu them being there is suppose to give us more room on the desktop.
Thank you

---

