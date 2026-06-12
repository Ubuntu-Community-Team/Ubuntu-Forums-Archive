---
title: "GTK 1.2 Fonts, lil' help"
date: 2006-05-06
forum: General Help
---

### Post by Onyros on 2006-05-06
Guys, I've ran out of ideas. I need your help: I've followed a whole lot of instructions to try making GTK 1.2 apps a little less ugly, but I haven't managed.

I have this problem with dillo, Audacity and XMMS, to name a few (it also happens with OpenOffice on Fluxbox, even though it does not happen in GNOME or KDE).

The fonts in these apps look like this (at the tab and address bar):
[[IMG]http://img401.imageshack.us/img401/4761/screenshot7ua.th.png[/IMG]](http://img401.imageshack.us/my.php?image=screenshot7ua.png)

I've tried *gtk-theme-switch* to no avail. I've tried changing *.gtkrc* and *.gtkrc.mine*, as well as *.gtkrc-1.2-gnome2*... nothing works.

This is what *.gtkrc.mine* looks like:
```
style "default-text"
{
  font="-adobe-helvetica-medium-r-normal-*-*-100-*-*-p-*-iso8859-2"
}
widget_class "*" style "default-text"
```. This output was created by gtk-theme-switch.

It doesn't make sense having this beautiful patched dillo with tabs, frames and anti-aliasing, and then having those mammoth, ugly fonts in gtk :P

---

