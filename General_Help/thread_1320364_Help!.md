---
title: "Help!"
date: 2009-11-09
forum: General Help
---

### Post by jeb800e on 2009-11-09
Please help me... on my Karmic PC, I was trying to set a screensaver, and my computer froze as soon as I clicked a certain one. I did the REISUB technique and rebooted the system, but now each time I go to choose the screensaver, it keeps on freezing. Is there a technique I can do to reset the screensaver to it's original state without going into the screensaver program?
Also, should I check my filesystem for errors or anything like that because I did REISUB, or does my computer automatically save its changes during REISUB? If so, how do I check my filesystem for errors?

Please help! Thanks!

---

### Post by catco_designs on 2009-11-09
alt+F2  gconf-editor  go to apps > gnome-screensaver.

---

### Post by jeb800e on 2009-11-09
what do I do from there?

---

### Post by NFblaze on 2009-11-09
change the line that says

*mode to "blank"*

and the line that says 

*theme to "screensavers-ubuntu_theme"*

I believe those are the defaults.


or you may just be able to uncheck the box for the *the idle_activation_enabled* key

---

### Post by jeb800e on 2009-11-09
I removed everything within the "Themes". Is that alright? It froze when I accidentally clicked the "random screensaver", so I had to remove everything. Also, the first time I had to remove another screensaver, but I don't remember which one. The screensavers still pop up, though, withing the "Screensaver" program under System > Preferences.
IS this all right, or should I change something again, etc.?

---

### Post by catco_designs on 2009-11-09
And [B]
Lock Delay[/B] = 0 (this is deault) 

**Theme** = screensavers-ubuntu_theme

[B]
Themes[/B]

The "Themes" key specifies the list of themes to be used by the screensaver. It's ignored when "mode" key is "blank-only", should provide the theme name when "mode" is "single", and should provide a list of themes when "mode" is "random". 

**Mode**

The selection mode used by screensaver. May be "blank-only" to enable the screensaver without using any theme on activation, "single" to enable screensaver using only one theme on activation (specified in "themes" key), and "random" to enable the screensaver using a random theme on activation.

---

### Post by jeb800e on 2009-11-10
Is is allright for me to remove all the things from the "themes" part?

---

### Post by catco_designs on 2009-11-10
Yes when "mode" key is "blank-only"

> **catco_designs said:**
> [B]
Themes[/B]

The "Themes" key specifies the list of themes to be used by the screensaver. It's ignored when "mode" key is "blank-only", should provide the theme name when "mode" is "single", and should provide a list of themes when "mode" is "random". 

**Mode**

The selection mode used by screensaver. May be "blank-only" to enable the screensaver without using any theme on activation, "single" to enable screensaver using only one theme on activation (specified in "themes" key), and "random" to enable the screensaver using a random theme on activation.

---

### Post by jeb800e on 2009-11-11
what if the mode isn't "blank only"?

---

### Post by catco_designs on 2009-11-11
> **jeb800e said:**
> what if the mode isn't "blank only"?
 					Originally Posted by **catco_designs** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8281794#post8281794") 				
 				[I][B]
Themes[/B]

The "Themes" key specifies the list of themes to be used by the screensaver. It's ignored when "mode" key is "blank-only", should provide the theme name when "mode" is "single", and should provide a list of themes when "mode" is "random". 

**Mode**

The selection mode used by screensaver. May be "blank-only" to enable the screensaver without using any theme on activation, "single" to enable screensaver using only one theme on activation (specified in "themes" key), and "random" to enable the screensaver using a random theme on activation.[/I]

---

### Post by Richiegs on 2009-11-13
When I press **Alt & F2**, a **Run Application** panel appears. I then choose** Gnome-screensaver**. What should I do next? Press **Run** button? When I use **Screensaver**, a lot of time it crashes or hangs. Please help

---

### Post by catco_designs on 2009-11-13
> When I press **Alt & F2**, a **Run Application** panel appears. I then choose** Gnome-screensaver**. What should I do next? Press **Run** button? When I use **Screensaver**, a lot of time it crashes or hangs. Please helpalt+F2  
***gconf-editor*** 
run
go to apps > gnome-screensaver

change the line that says

*mode to "*blank-only*"*

and the line that says 

*theme to "screensavers-ubuntu_theme"*

> **catco_designs said:**
> And [B]
Lock Delay[/B] = 0 (this is deault) 

**Theme** = screensavers-ubuntu_theme

[B]
Themes[/B]

The "Themes" key specifies the list of themes to be used by the screensaver. It's ignored when "mode" key is "blank-only", should provide the theme name when "mode" is "single", and should provide a list of themes when "mode" is "random". 

**Mode**

The selection mode used by screensaver. May be "blank-only" to enable the screensaver without using any theme on activation, "single" to enable screensaver using only one theme on activation (specified in "themes" key), and "random" to enable the screensaver using a random theme on activation.

---

