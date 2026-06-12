---
title: "(GNOME3) Screenlets disapears with show desktop shortcut"
date: 2011-12-11
forum: General Help
---

### Post by emptycoder on 2011-12-11
Hello everyone.
I'm having a problem with Screenlets, it disappears (or should I say minimize) when I hit Show Desktop shortcut.
I tried hide_skip_taskbar_windows method but for unknown reasons, it didn't work, also I tried Treat as Widget but still no luck.
I'm using Ubuntu 11.10 x64 with GNOME 3 shell.
Thanks a lot.

---

### Post by linux_paul on 2011-12-21
I'm interested in using screenlets in 11.04 with Gnome 3 too. Is this the only issue you've encountered?

---

### Post by rajtendulkar on 2012-04-17
Hello,

I am facing the same problem and tried to solve it but no success. :(
I am using Gnome Fallback Session.
   
I read in a post to uncheck compiz-settings-manager --> hide skip taskbar windows.
It did not work for me.

In another post, I read that the compiz manager settings have to be refreshed explicitly.
It was suggested to install Fusion-Icon to refresh them from the system tray.
I did that and the thing worked !
But the Fusion-Icon changed settings(by adding some effects) and slowed my computer a bit.
Hence I uninstalled it and again the thing does not work.

Could anyone help me out Please?

Thank You !
Raj

---

### Post by stinkeye on 2012-04-17
This is a workaround I found when not running compiz.
In the terminal...
```
gksudo gedit /usr/share/pyshared/screenlets/__init__.py
```

There is a section starting at line 957
> if os.environ.get('DESKTOP_SESSION') == "ubuntu":
				self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)
#			elif os.environ.get('DESKTOP_SESSION') == "ubuntu-2d":
#				self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_UTILITY)
#			elif os.environ.get('DESKTOP_SESSION') == "gnome":
#				self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_UTILITY)
			else:
				#self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_UTILITY)
			#self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_TOOLBAR)
			 [COLOR="Red"]#[/COLOR]self.window.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)

Remove the [COLOR="Red"]#[/COLOR] from the last line in that section
and save.

Restart the screenlet and see if it hides with show desktop.

---

### Post by rajtendulkar on 2012-04-17
Wow !!! 
This worked !!! :)
Thanks a lot Sire.. !! :D

---

### Post by rajtendulkar on 2012-06-28
This file though gets overwritten again and again from somewhere for every boot.
Can I modify it in original source

---

### Post by Monotoko on 2012-06-28
I'm not so sure about the original source of the overwrite, but a quick hack to fix it would be to have a script run after the initial boot.

Put a copy of the correct file into your home, then edit /etc/rc.local and just do a "cp /home/[COLOR="Red"]username[/COLOR]/initscript.py /usr/share/pyshared/screenlets/__init__.py" and make sure you end it with "exit 0" - replacing username with your actual username.

---

### Post by rajtendulkar on 2012-06-28
okay ! 
thanks !

---

