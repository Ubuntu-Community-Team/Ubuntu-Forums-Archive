---
title: "Missing Icons - Min, Max Close"
date: 2010-03-20
forum: General Help
---

### Post by p2cd3 on 2010-03-20
After the last daily update using 9-10, I have lost sight of my Min, Max & Close icons to all programs

How do I get these icons back & not have it happen again

TIA

---

### Post by Jay Car on 2010-03-20
> **p2cd3 said:**
> After the last daily update using 9-10, I have lost sight of my Min, Max & Close icons to all programs

How do I get these icons back & not have it happen again

TIA

I know this might sound like a silly question, but...

Are those min-max-close buttons really *gone*, or are they just hiding on the left side of the window bar (where you might not have expected to see them)?

If so, here's a possible fix:
[Easy GUI Window Button Switcher for Lucid (and Karmic) users]("http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html")

And here's another from Ubuntu member, iRock:
> **iRock said:**
> Post this in a terminal and it will put the buttons back where they belong. ```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

I hope this helps. :)

---

### Post by p2cd3 on 2010-03-20
Thanks Jay Car

I did both examples & still no icons

---

### Post by dcstar on 2010-03-20
> **p2cd3 said:**
> After the last daily update using 9-10, I have lost sight of my Min, Max & Close icons to all programs

How do I get these icons back & not have it happen again

TIA

[LIST=1]
[*]Why does your profile show 7.10?
[*]Try turning of desktop effects
[/LIST]

---

### Post by p2cd3 on 2010-03-20
Desktop effects are off

---

### Post by Brandel Valico on 2010-03-20
May have something to do with this issue

[http://ubuntuforums.org/showthread.php?t=1434160](http://ubuntuforums.org/showthread.php?t=1434160)

If this seems to fit your issue 

Try this its a workaround provided by Nightwishfan

Workaround for a usable desktop:
Log in and press ctrl+alt+t to get a terminal, type:
Code:

> gnome-panel

Press alt+f2 and type:
Code:

> nautilus

Desktop should be usable, do not close terminal. You may also be able to press alt+f2 again and run:
Code:

> killall gnome-terminal && gnome-terminal

See how it works for you.

---

### Post by p2cd3 on 2010-03-20
Brandel Valico, nothing has changed

Will wait for next update & hope all is back to normal

The reason I left Gentoo 3 years ago was for this very reason - having to re-config after every update

---

