---
title: "Window management in Kubuntu 9.10"
date: 2010-01-19
forum: General Help
---

### Post by Crowchild on 2010-01-19
I've just made the switch from Ubuntu to Kubuntu and would like to maintain some of the functionality that I am used to in gnome. In particular, I'd like to rotate the between desktops with ctrl-alt-left and ctrl-alt-right.
I'd also like to find something the ring switcher and shift switcher. Previously, I had them set up so that I would switch between window on one desktop with the shift switcher and between all the windows on all the desktops with the ring switcher.

So far I like the look and feel of Kubuntu with Kwin and would like to stick with it. So, it would be awesome if someone could show me how to set these up!

Thanks.

---

### Post by kellemes on 2010-01-19
> **Crowchild said:**
> I've just made the switch from Ubuntu to Kubuntu and would like to maintain some of the functionality that I am used to in gnome. In particular, I'd like to rotate the between desktops with ctrl-alt-left and ctrl-alt-right.
I'd also like to find something the ring switcher and shift switcher. Previously, I had them set up so that I would switch between window on one desktop with the shift switcher and between all the windows on all the desktops with the ring switcher.

So far I like the look and feel of Kubuntu with Kwin and would like to stick with it. So, it would be awesome if someone could show me how to set these up!

Thanks.

I assume you've been at Desktop Settings -> All Effects?
Since you're using Kwin these are the effects/features you have to deal with.. already a lot but not yet all you get with Compiz.
If you want the same stuff as with your Gnome-setup, you have to replace Kwin with Compiz and use ccsm (CompizConfig Settings Manager) to set it up as you wish.

---

### Post by Crowchild on 2010-01-19
Yeah, I found "Desktop Settings -> All Effects"

Maybe I should rephrase my question: More than anything I would like to easily move between desktops and windows with a keyboard short cut but I can seem to find anything that allows me to set these up.
I don't necessarily need the rotating cube or the ring switcher...

thanks again.

---

### Post by garryknight on 2010-01-19
System Settings, Keyboard and Mouse, Global Keyboard Shortcuts, select KWin from the dropdown menu at the top of the right-hand pane. Scroll down until you find "Switch to next desktop". Click the entry, then click the button to the right of "Custom". Press the key combination you want to use, then click the "Switch to next desktop" text. Scroll down to "Switch to previous desktop" and repeat the procedure. Click the Apply button to finish.

---

### Post by lykwydchykyn on 2010-01-19
Open "system settings->computer administration->keyboard & mouse -> Global Keyboard Shortcuts".

Select kde component KWin.

Scroll down a bit and you'll see "Switch One Desktop Down", "Switch One Desktop to the Left", etc.  These have no shortcut by default, but you can set one by clicking and changing the shortcut to "custom" then setting a shortcut (yeah, it's hard to describe but self-evident when you see it).

One thing you have to understand though is that KDE, unlike compiz, maps out your desktops to match the layout of your pager.  In other words, if you have your desktops in a 2x2 grid, you don't just navigate left and right through all desktops.  You have to navigate up and down too.  I don't remember if this can be changed, but it's default.

EDIT: Garryknight beat me to it.

---

### Post by Crowchild on 2010-01-19
Yeah, I don't mind that it's a 2x2 grid... I just wanted a simple way to get between the desktops. What you've suggested works great!

Any suggestions for the window switcher?

Thanks everyone.

---

### Post by lykwydchykyn on 2010-01-19
> **Crowchild said:**
> Yeah, I don't mind that it's a 2x2 grid... I just wanted a simple way to get between the desktops. What you've suggested works great!

Any suggestions for the window switcher?

Thanks everyone.

Does alt-tab not work?

---

### Post by garryknight on 2010-01-19
> **lykwydchykyn said:**
> 
One thing you have to understand though is that KDE, unlike compiz, maps out your desktops to match the layout of your pager.  In other words, if you have your desktops in a 2x2 grid, you don't just navigate left and right through all desktops.  You have to navigate up and down too.  I don't remember if this can be changed, but it's default.


The only setting I know is in the Desktop, Desktop Effects, All Effects, Window Management, Desktop Cube Animation configuration dialog, which has a "Use pager layout for animation" setting. But if he sets the "Switch to next desktop" and "switch to previous desktop" keypresses, they will switch through all desktops linearly, e.g. with 4 desktops, repeated pressing of "Switch to next" will go through 1, 2, 3, 4, 1, 2, and so on, and "Switch to previous" will do the same in reverse order.

---

