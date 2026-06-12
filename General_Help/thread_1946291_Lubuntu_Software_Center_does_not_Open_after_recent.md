---
title: "Lubuntu Software Center does not Open after recent Update"
date: 2012-03-24
forum: General Help
---

### Post by 2CV67 on 2012-03-24
I noticed Lubuntu Software Center was updated several times recently and now it has stopped opening at all.

I found the FAQ/workaround item here:
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Lubuntu_Software_Center_not_working](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds#Lubuntu_Software_Center_not_working)

& ran "lubuntu-software-center" with the following result

```
chris@Acer-desk:~$ lubuntu-software-center

(lubuntu-software-center:2633): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
Opening config file
Opening config file
Traceback (most recent call last):
  File "/usr/bin/lubuntu-software-center", line 35, in <module>
    mainfunc()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 679, in lscmain
    app = LscControl()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 49, in __init__
    self.ui = UI.Gui(self.on_selected_category, threadingops.get_categories())
  File "/usr/lib/python2.7/dist-packages/LSC/UI.py", line 71, in __init__
    self.pages = pages.Pages(categories_func)
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/pages.py", line 44, in __init__
    self.appsinfo = appsinfo.InfoBox()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 39, in __init__
    self.screendesc = ScreenDesc()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 97, in __init__
    self.details = Details()
  File "/usr/lib/python2.7/dist-packages/LSC/widgets/appsinfo.py", line 148, in __init__
    self.arrow = Gtk.Arrow(Gtk.ArrowType.RIGHT, Gtk.ShadowType.NONE)
TypeError: GObject.__init__() takes exactly 0 arguments (2 given)
chris@Acer-desk:~$
```

I tried "rm -r /home/chris/.config/lsc" but that did not have any effect.

I used Synapt to completely remove LSC then reinstalled it after a reboot, but it still does not open...

Ideas please?

Thanks!

---

### Post by 2CV67 on 2012-03-31
After yet another update, LSC is now working OK again.

---

