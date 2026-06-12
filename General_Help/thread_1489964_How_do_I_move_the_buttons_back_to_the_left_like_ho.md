---
title: "How do I move the buttons back to the left like how the default 10.04 buttons are?"
date: 2010-05-21
forum: General Help
---

### Post by TheNerdAL on 2010-05-21
I was trying some new themes and they moved it to the right, I want them back to the left, thanks.

---

### Post by ShadowMage on 2010-05-21
In Lucid the theme determines/changes the button layout, but once you have selected a theme you can customize the button layout using Ubuntu Tweak: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

In Ubuntu Tweak this can be achieved by going to "Window Manager Settings" and customizing the "Window Titlebar Button Layout" section. I've played around with it and it works like a charm. Note that after customizing the "Window Titlebar Button Layout", if you change themes again the theme will set the button layout back to the theme's default.

If you need help with this let me know.

---

### Post by bumanie on 2010-05-21
Follow [this]("http://www.everyjoe.com/newlinuxuser/move-your-metacity-buttons-in-gnome/"). basically you have to move the colon from where it is now, which should be on the left of the words  close,minimize,maximize to the right side of those words (once in gconf-editor as described in the link).

---

### Post by 2hot6ft2 on 2010-05-21
The best method is explained here along with more info. about the move.
[Known Lucid Lynx issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1469475")
> **philinux said:**
> 
**[COLOR="DarkRed"]Minimize, Maximize and Close button placement.[/COLOR]**
A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.
**[Update ][http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)**

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
**Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders.  Unfortunately, if the wrong approach spreads, they won't be able to do that.**

:popcorn:

---

### Post by TheNerdAL on 2010-05-21
> **ShadowMage said:**
> In Lucid the theme determines/changes the button layout, but once you have selected a theme you can customize the button layout using Ubuntu Tweak: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

In Ubuntu Tweak this can be achieved by going to "Window Manager Settings" and customizing the "Window Titlebar Button Layout" section. I've played around with it and it works like a charm. Note that after customizing the "Window Titlebar Button Layout", if you change themes again the theme will set the button layout back to the theme's default.

If you need help with this let me know.

Thanks!

---

### Post by robbie d on 2010-05-22
Gconf editing worked for me, now how can I make them Red, etc........... ;)
Are there plans to move the menus from each app into the filebar up the top?

---

