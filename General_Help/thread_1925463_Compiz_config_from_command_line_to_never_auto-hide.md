---
title: "Compiz config from command line to never auto-hide bar"
date: 2012-02-14
forum: General Help
---

### Post by Kissell on 2012-02-14
I hate that the unity bar is on the left and auto-hides by default.  This really gets in the way of copying text in a maximized text editor.

I found a solution, tell it to never hide, but it requires I install compiz settings manager and use the mouse to configure it.

Is there a way I can tell the unity bar to never hide from the command line?  I want to put that into my install script along with everything else, so there are no changes I need to make every time I install Ubuntu.  I can install compiz from my script, but I don't know how to configure the unity plugin from the command line so that it won't hide that bar.

The setting in the GUI is the unity plugin in compiz, then the "hide launcher" setting to "never"

---

### Post by Krytarik on 2012-02-14
You can use "[gconftool-2]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/gconftool-2.1.html")" to change GConf settings via command line; in your case it would be like this:
```
gconftool-2 --set --type int /apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode 0
```
Possible values of that key are:

[LIST]
[*]"0": Never Hide (as set up above)
[*]"1": Auto-Hide
[*]"2": Dodge Windows
[/LIST]
But notice that these are monitor-specific settings, like in other places of Compiz' settings also, where "screen0", like in the above command, corresponds to the first monitor, "screen1" to the second, and possibly more.

Regards.

---

### Post by Kissell on 2012-02-14
Thanks.  That works great...  

As another note, you can find other paths to other settings to change using the configuration editor in unity.  I used gconftool for other things, just didn't realize I could also control compiz plugins from it.
  
BTW: it is user specific...  for instance, if I run it with "sudo" it doesn't work at all.

---

### Post by Kissell on 2012-02-14
Do you happen to know how I can turn on and off entire plugins in compiz from the command line?  

I can use this trick to change their settings, but don't see where to turn a plugin off or how to turn on one I've installed.

edit: Never mind: Google found that one pretty quick.
"/apps/compiz-1/general/screen0/options/active_plugins"

---

