---
title: "Font Color - Top Panel. Change?"
date: 2010-02-15
forum: General Help
---

### Post by Roasted on 2010-02-15
I have a custom theme on my Ubuntu computer here. It's a theme where I can customize any of the color settings, so nothing is locked. The top panel has slightly darker text than I'd like, so I'd like to lighten it up a bit. The thing is no matter what text color option I change in the theme settings, none make a difference. 

Can I do this somewhere in the system settings, or does it HAVE to be controlled from the theme itself?

---

### Post by stinkeye on 2010-02-15
Try gnome-color-chooser.

---

### Post by Roasted on 2010-02-15
Worked like a charm. Thanks bro!

I assume it overrides any theme settings??

---

### Post by stinkeye on 2010-02-15
> **Roasted said:**
> Worked like a charm. Thanks bro!

I assume it overrides any theme settings??

Yes , it overrides theme settings.

Writes a line to your  ~/.gtkrc-2.0 file 
```
include ".gtkrc-2.0-gnome-color-chooser"
```

which points to your ~/.gtkrc-2.0-gnome-color-chooser file
that will look something like this
```
pixmap_path "/home/glen/.gnome-color-chooser/images/"

style "gnome-color-chooser-panel"
{
  fg[NORMAL] = "#B9CDD5"
  font_name = "GE Inspira Bold 12"
}
class "PanelTopLevel.*" style "gnome-color-chooser-panel"
widget_class "*PanelApplet*" style "gnome-color-chooser-panel"
widget_class "*PanelWidget*" style "gnome-color-chooser-panel"
widget "*fast-user-switch-applet*" style "gnome-color-chooser-panel"

style "gnome-color-chooser-window-decoration"
{
  bg[SELECTED] = "#A39E9E"
}
class "GtkWindow" style "gnome-color-chooser-window-decoration"

```

---

### Post by Roasted on 2010-02-15
There's so many dark themes I like that use gray-ish colored text in the top panel. And while I understand why, I still like to see bright white text on black/darker themes. So it's nice having the option with gnome color chooser to do so.

While we're throwing a spin on things, does KDE have a color chooser?

---

### Post by HuXu on 2010-03-09
I used that but it only changed my Date and Time font color.  My menus remain the old color.

---

### Post by Kom-Si on 2010-10-20
thnx a lot - finally found a way to make panel font bold.

---

