---
title: "Gnome-Menu description?"
date: 2009-09-20
forum: General Help
---

### Post by Tom Mann on 2009-09-20
Hi all,
I'm posting this from Ubuntu 9.10 Alpha 6, though imagine my question applies to earlier versions.

I have set my Gnome session up the way I like it... Almost.

I have this...
[IMG]http://lh4.ggpht.com/_zkkDhfmxlHI/SraT9g2DueI/AAAAAAAABEc/Ipm_OvptASo/s800/Screenshot.png[/IMG]

But want my start button more like this...
[IMG]http://lh4.ggpht.com/_zkkDhfmxlHI/SraTCZA4OwI/AAAAAAAABEU/Tl-AOCQ5RV8/s144/ubuntu_menu.png[/IMG]

Does anyone here know what I need to do to achieve this?
Thanks, T :KS

---

### Post by Tipped OuT on 2009-09-20
It's not possible with that menu launcher.

---

### Post by Yvan300 on 2009-09-20
Maybe you could create a svg icon with your particular menu then use it in gno-menu, not sure how you do that anyway :(

---

### Post by Tipped OuT on 2009-09-20
> **Yvan300 said:**
> Maybe you could create a svg icon with your particular menu then use it in gno-menu, not sure how you do that anyway :(

He could do that, but I believe the icon wouldn't show at the correct size. It would be shrunken to the point the text was unreadable.

---

### Post by ibuclaw on 2009-09-20
> **Tom Mann said:**
> Hi all,
I'm posting this from Ubuntu 9.10 Alpha 6, though imagine my question applies to earlier versions.

I have set my Gnome session up the way I like it... Almost.

I have this...
[IMG]http://lh4.ggpht.com/_zkkDhfmxlHI/SraT9g2DueI/AAAAAAAABEc/Ipm_OvptASo/s800/Screenshot.png[/IMG]

But want my start button more like this...
[IMG]http://lh4.ggpht.com/_zkkDhfmxlHI/SraTCZA4OwI/AAAAAAAABEU/Tl-AOCQ5RV8/s144/ubuntu_menu.png[/IMG]

Does anyone here know what I need to do to achieve this?
Thanks, T :KS

Inside your icon directory, copy it in and name it "**start-here.png**"

ie: The location of my start menu icon is
```
~/.icons/Crashbit-ubuntu/24x24/places/start-here.png
```
But I'm not sure you can have anything beyond 24x24 though.

Regards
Iain

---

### Post by Tom Mann on 2009-09-20
Mint managed it. I found a way on the net ages ago but was never able to find it again...

Mint:
[IMG]http://www.linuxmint.com/img/screenshots/gloria/14.png[/IMG]

The SVG thing could be a problem as I like to change my themes, and will have to change the SVG's text colour to contrast with the background.

---

### Post by Tipped OuT on 2009-09-20
> **Tom Mann said:**
> Mint managed it. I found a way on the net ages ago but was never able to find it again...

Mint:
<snip>

The SVG thing could be a problem as I like to change my themes, and will have to change the SVG's text colour to contrast with the background.

[http://www.flyninja.net/?p=888](http://www.flyninja.net/?p=888)

---

### Post by Tom Mann on 2009-09-20
Hi Tipped - I think that applies to the standard Ubuntu menu (Application, Places, System)...

---

### Post by Tom Mann on 2009-09-21
Sorry to bump, but... Anyone? :confused:

---

### Post by Tipped OuT on 2009-09-21
No, sorry man. That was all I could come up with. Maybe you should ask at the Mint forums?

---

### Post by Tom Mann on 2009-09-23
Tipped ouT, I'm going to use your link to try and adjust the main menu applet to include text. If I succeed I may post it in here and point launchpad and making it all nice and i18n'd :)

Really really surprised the option doesn't exist. :(

---

