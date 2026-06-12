---
title: "WxWidgets 2.9"
date: 2010-07-27
forum: General Help
---

### Post by ks07 on 2010-07-27
Hey,
I'm trying to compile a program but it depends on the latest version of wxwidgets, which is 2.9 and is not in the repos. I have downloaded the source and attempted to build it, which seems to have worked but I have no idea what to do next. It seems to be a bit harder than the usual make && make install... Anybody tried installing wxwidgets 2.9? OR even better, does anybody know of a pre-compiled .deb? (wishful thinking)

Thanks :)

---

### Post by hiacynt on 2010-11-04
Since many wxW apps use wx-config to get the proper compilation/linking paths and flags, you need to make sure your system uses the wx-config from the 2.9 version. First of all check which one you have installed - you can do this by running 'wx-config --version' from the terminal.
If it says 2.9.X then you're good, otherwise, you need to replace the old one with the copy present in the directory where you extracted the wxW-2.9 source.
Usually the files that you need to replace are:
[LIST]
[*]/opt/wx/2.8/bin/wx-config
[*]/usr/local/bin/wx-config
[/LIST]
Although I am not 100% sure if that's the complete list.

---

### Post by cchhrriiss121212 on 2010-11-04
Maybe this is some help:
[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

---

