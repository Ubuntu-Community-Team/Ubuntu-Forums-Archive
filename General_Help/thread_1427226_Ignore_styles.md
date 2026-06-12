---
title: "Ignore styles"
date: 2010-03-11
forum: General Help
---

### Post by wirate on 2010-03-11
How can i make an application ignore widget style configurations in kde? Like Synaptic and some other applications do.

---

### Post by swoll1980 on 2010-03-11
> **wirate said:**
> How can i make an application ignore widget style configurations in kde? Like Synaptic and some other applications do.

The apps that are ignoring it are probably GTK apps written for the Gnome desktop environment. I know Synaptic is. They use a different theme engine.

---

### Post by Intrepid Ibex on 2010-03-11
Ummm... I guess you are talking about **qt** *(kde)* and **gtk+** *(gnome, lxde, xfce, etc.)* **GUIs** that different apps use? E.g. **Synaptic** and **firefox** uses **gtk+**, while the native **KDE** apps use **qt** *(these things have different settings and themes)*. There is no way to *ignore* the theming you specify yourself in the **Appearance section** of the **KDE System Settings** *(unless running the app as a different user because different users have their own appearance configurations)*.

So you just need to configure your apps looks in the **KDE System Settings**.

---

### Post by Dragonbite on 2010-03-11
What about looking at [_gtk2-engines-qtcurve_]("http://packages.ubuntu.com/karmic/gtk2-engines-qtcurve")> This package together with kde-style-qtcurve aim to provide a unified look and feel on the desktop when using KDE and GNOME applications.

This package is most useful when installed together with kde-style-qtcurve. 

Or [_kcm-gtk_]("http://packages.ubuntu.com/karmic/kcm-gtk")> This is a configuration module for System Settings for configuring the widget style and fonts of GTK+ applications in KDE. It is derived from gtk-qt-engine's configuration module. 

---

### Post by wirate on 2010-03-12
Thanks everyone. I noticed that programs being run as root have a different appearance because root has a different configuration. Well I want to run amarok as root because amarok doesnt like my bespin configuration. I can do that in konsole by "sudo amarok" but I want to make a graphical launcher for this purpose.

Thanks again

---

