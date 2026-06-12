---
title: "Ambiance highlight colour won't change"
date: 2012-05-05
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-05
Some time ago I posted a [thread asking how to change the Ambiance theme's orange colour]("http://ubuntuforums.org/showthread.php?t=1927012"). I decided to try the solution posted [in this reply]("http://ubuntuforums.org/showpost.php?p=11696472&postcount=6"), and it worked.

Then later on, I tried using [themes published here]("http://www.webupd8.org/2012/01/ambiance-and-radiance-colors-theme-pack.html"), and they don't work on the computer on which I performed the mentioned colour change. No matter which theme I select, the highlight colour remains unchanged. Although the window buttons (close, minimize, maximize) change their colours, the highlight colour doesn't change.

On another computer with Ubuntu 12.04 the new themes work alright.

---

### Post by mc4man on 2012-05-05
The gsetting is overriding any other selected_bg color. So set back default of nothing set

```
gsettings set org.gnome.desktop.interface gtk-color-scheme ""
```

Or open dconf-editor, find the key, highlight it & click on 'set to default'

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-05
Sweet, that worked. Thanks a lot!

---

