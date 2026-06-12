---
title: "How to get back transparent icon labels on desktop (xubuntu 12.04)?"
date: 2012-06-24
forum: General Help
---

### Post by cbraxton on 2012-06-24
Not a major issue, but annoying nonetheless...

I was playing around with desktop settings in xubuntu 12.04, changing background image, icon size, and font size. All of a sudden the desktop icon labels are no longer transparent, they have background boxes as though they've been selected via mouse click. (Image attached -- actually selecting an icon turns the text background darker.) There does not appear to be anything in the desktop settings GUI having to do with this.

Google searches turned up articles recommending editing or creating ~/.gtkrc-2.0 to enable transparent icon labels. There was no such file, I created one with the contents suggested by a few articles but so far have had no luck.

Anyone know how to get the transparent labels back?

---

### Post by cbraxton on 2012-06-24
This was for Xubuntu 12.04, I've marked the prefix "Solved." I seem to be doing this a lot lately, posting a question and finding the answer myself a few minutes later.

It turns out that in addition to adding/editing the .gtkrc-2.0 file (contents below), it is necessary to go into the "Appearance" section of "Settings" and change the theme for the change to take effect. Rebooting didn't do it, had to change the theme to something else, then back again to what I wanted. Bizarre, but simple enough to do.

```

# Contents of ~/.gtkrc-2.0

style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 0

base[NORMAL] = "#000000"
base[SELECTED] = "#000000"
base[ACTIVE] = "#000000"

fg[NORMAL] = "#ffffff"
fg[SELECTED] = "#ffffff"
fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

---

### Post by vasa1 on 2012-06-24
> **cbraxton said:**
> This was for Xubuntu 12.04, I've marked the prefix "Solved." I seem to be doing this a lot lately, posting a question and finding the answer myself a few minutes later.
...
It's a perfectly legitimate question and you provided the answer as well so I'm not seeing anything to be apologetic about.
Many converts to Xfce have had the same question :)

---

