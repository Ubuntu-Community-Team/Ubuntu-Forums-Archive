---
title: "moving window causes it to maximize"
date: 2011-06-25
forum: General Help
---

### Post by JBA2337 on 2011-06-25
I recently installed Ubuntu 11.04. It exhibits a rather strange behavior that is rather annoying and frustrating.

On the Desktop I adjusted a window to the size that I want. Then I move the windows by dragging it by the title bar. When I move the window to the location I want it and then release the mouse, the window immediately maximizes. In other words, if I resize the window and then move it anywhere on the desktop, it automatically maximizes.

Is there a setting where I can stop this behavior?

Thanks!

JBA2337

---

### Post by Abir Valg on 2011-06-25
Has it always been like that?
Seems like your touchpad driver thinks that left button release is a double click.
Could you click the left button and release it over a folder in a file manager (nautilus) - see if it does really trigger a double-click and opens that folder.

---

### Post by JBA2337 on 2011-06-26
I only noticed this behavior, shortly after I installed Ubuntu 11.04, which was last week.

More detail:

I discovered that if I drag a window around, when I move the window to the top of my laptop's screen and then release the left mouse button the window automatically maximizes. This happens with any window, including nautilus.

I can drag a window anywhere I want to, and it does not maximize, as long as I don't drag the window to the top of the screen.


JBA2337

---

### Post by dFlyer on 2011-06-26
It only win max the screen on my system if I push it on top of the top panel and let go of the mouse. I can drag and drop it any where on the desktop without it going max, just as long as I don't try to force it to the top panel. Don't know if it's a feature or a bug with Unity, but has been going on since at least beta1 when I started using unity.

---

### Post by CompBio on 2011-07-02
I've noticed the same (unwanted) behavior: move a window to the top or bottom of the screen and it maximizes.  If anyone finds a fix for this, please post!

---

### Post by wildmanne39 on 2011-07-02
Hi,it is a feature. I think it can be changed in ccsm, but I am not sure which setting has to be changed, I changed mine when I was testing natty beta, so I just do not remember, but do not uncheck unity plugin.

---

### Post by coffeecat on 2011-07-02
This is a feature, not a bug. In fact it mimics the same behaviour in Windows 7. 

> **CompBio said:**
> I've noticed the same (unwanted) behavior: move a window to the top or bottom of the screen and it maximizes.  If anyone finds a fix for this, please post!

If your app windows are being maximised when you move them to the bottom of the screen, then you must have changed the settings in ccsm. The default behaviour when windows are moved to the bottom of the screen is nothing.

Open compiz config settings manager > Window management > grid > Edges tab. See my screenshot. Change your settings according to your preference.

But before you do so, try this. Open two applications, the sort of applications you might want to sit side-by-side. Drag one beyond the right edge of the screen and let go at the point the mouse cursor touches the edge of the screen. Now do the same to the other app but at the left edge of the screen. Useful - yes? Now drag them back again.

---

### Post by JBA2337 on 2011-07-17
In my opinion, a pretty dumb idea...to automatically maximize a window when you move it to the top of the screen

Anyway, I solved the problem myself, and the solution is rather easy.

Open the Configuration Editor (the terminal command is **gconf-editor**). Now click on Edit>Find, and search for **top_edge_action**. The default value is 10 (maximize). Right click on this key, then click on EDIT. Change the value from 10 to 0. Save it, and problem solved...no more automatic maximization.

JBA2337

---

