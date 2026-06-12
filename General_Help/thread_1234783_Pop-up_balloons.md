---
title: "Pop-up balloons"
date: 2009-08-08
forum: General Help
---

### Post by DeMus on 2009-08-08
In an attempt to increase the free space on my desktop I set the bottom panel to auto-hide.
Now every time I pull the cursor all the way down, the panels pops up, which is good.
Only, the buttons which are on there are hidden behind a yellow balloon telling me which one the mouse is currently pointing at. The ones next to that one are covered by the balloon, so I don't know which one to click.
How do I switch off those annoying balloons? That was one fo the first things I did after installing a Windows system: switching off the balloons.
Maybe they are useful, but not to me.

---

### Post by dagrump on 2009-08-08
Alt+f2 & gconf-editor, then under apps find panel, disable tool tips.
That should do it.

---

### Post by DeMus on 2009-08-08
> **dagrump said:**
> Alt+f2 & gconf-editor, then under apps find panel, disable tool tips.
That should do it.

Thank you for your answer. Maybe it should do it, but until now it doesn't. I went through all the different items in app/panel but even when I uncheck the box the yellow tips still keep coming.
Which one should I disable? And should I restart afterwards or does it change instantly?

---

### Post by dagrump on 2009-08-08
Well I thought that would take care of it. I've never bothered with it before as I'm using large monitors most of the time. I'll snoop around some more, as it might be useful on my baby laptop.

---

### Post by dagrump on 2009-08-08
Well, sorry that only seems to work on the launchers I've added to the top panel & doesn't effect the default panel junk. ie clock, desktop switcher, etc...
I'm no help, I tried but no cigar. Good luck & if you find a way be sure to add it here, it might be real handy on little screens.

---

### Post by DeMus on 2009-08-08
> **dagrump said:**
> Well, sorry that only seems to work on the launchers I've added to the top panel & doesn't effect the default panel junk. ie clock, desktop switcher, etc...
I'm no help, I tried but no cigar. Good luck & if you find a way be sure to add it here, it might be real handy on little screens.

Got it:

On [_**Turn off tooltips**_]("http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html") Anonymous wrote:


THIS HOW YOU TURN OFF TOOLTIPS!

1) Find the folder of your current theme. Its located either in ~/.themes/gtk-2.0 or /usr/share/themes/[COLOR="Red"]used themename[/COLOR]/gtk-2.0

2) Here you will find a file called gtkrc. Open it with your favorite editor.

3) Look for this section: # tooltips stuff
widget "gtk-tooltip*" style "theme-tooltips"

4) Add this line:

gtk-enable-tooltips = 0

5) Save the changes and reload your theme, or reboot.

I did not have the tooltip stuff section in my used theme so I added the line here:
```
}
[COLOR="Red"]gtk-enable-tooltips = 0[/COLOR]

style "theme-tooltips" = "theme-wider"
{
	bg[NORMAL] = @tooltip_bg_color
	fg[NORMAL] = @tooltip_fg_color
  engine "clearlooks"  
  {
}
```

---

### Post by dagrump on 2009-08-08
Very good, I'll have to remember that & try it on an AA1s, Need all the space you can get on those things.:)

---

