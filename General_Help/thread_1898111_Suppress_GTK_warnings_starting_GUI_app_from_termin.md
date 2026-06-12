---
title: "Suppress GTK warnings starting GUI app from terminal?"
date: 2011-12-20
forum: General Help
---

### Post by brec on 2011-12-20
I access my Ubuntu 11.10 system mostly via ssh -X from my Mac.  I like this because it gives me convenient terminal window access and when on occasion I want to run a GUI application I can start it from the terminal and the Mac's X client will show the app's window.  All well and good except for one nuisance:  starting a GUI app this way usually clutters the terminal with inconsequential errors or warnings such as these (for Chromium Browser):

```
(chromium-browser:2233): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:2233): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:2233): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:2233): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

Is there a way to suppress them?

---

### Post by pytheas22 on 2011-12-20
Redirecting the output to /dev/null should probably work, e.g.:
```

chromium-browser &> /dev/null
```

---

### Post by brec on 2011-12-20
> **pytheas22 said:**
> Redirecting the output to /dev/null should probably work, e.g.:
```

chromium-browser &> /dev/null
```

s/probably//

Also, I add " &" at the end to get the terminal back while the app's window is up.

Is there a good way to do this on commands which take an argument, e.g., gedit foobar.txt, while minimizing typing?

---

### Post by pytheas22 on 2011-12-20
> Is there a good way to do this on commands which take an argument, e.g., gedit foobar.txt, while minimizing typing? 

Not that I know of, I'm afraid--though others know more than me.

If you check man pages some applications may provide command-line flags for suppressing CLI output, but that's a rare option for GUI applications.

There may be other remote-desktop solutions that would work better for what you're trying to do by letting you forward individual application windows over the network, rather than the whole desktop.  That way you wouldn't have to worry about launching stuff via ssh in a terminal.  Quick googling turned up [this]("http://shared-app-vnc.sourceforge.net/"), for instance, though I'm not sure how mature it is.

---

### Post by brec on 2011-12-20
> **pytheas22 said:**
> 
... There may be other remote-desktop solutions that would work better for what you're trying to do by letting you forward individual application windows over the network, rather than the whole desktop.  That way you wouldn't have to worry about launching stuff via ssh in a terminal.  Quick googling turned up [this]("http://shared-app-vnc.sourceforge.net/"), for instance, though I'm not sure how mature it is.

My current solution, ssh -X, i.e., ssh with X11 forwarding, does not forward the whole desktop.  It forwards only the contents of individual windows, and my Mac's X11 application displays those windows.  (The X11 client on my Mac is automatically invoked when necessary.)  That I see only individual windows is the problem, although it's not a big one. Since I don't have a Ubuntu desktop while using ssh, I don't have desktop menus, etc., from which to launch GUI apps.

For apps I use frequently I make bash aliases.  If I don't know the app's binary's name, I open the desktop's menu editor (via ssh!)  and look at the app's menu properties, which include the CLI command to open it.

E.g.
alias menus='/usr/bin/python -OOt /usr/bin/alacarte &> /dev/null &'
...so I type "menus" in my Mac's terminal window to open the window of Ubuntu's desktop menu editor.

---

### Post by Derek Karpinski on 2011-12-21
```
sudo apt-get update && sudo apt-get install gtk2-engines-pixbuf
```

---

### Post by brec on 2011-12-21
> **Derek Karpinski said:**
> ```
sudo apt-get update && sudo apt-get install gtk2-engines-pixbuf
```

The only info I could find via Google on this package is "This package contains the pixbuf theme engine."

Oh.

---

### Post by pytheas22 on 2011-12-21
> My current solution, ssh -X, i.e., ssh with X11 forwarding, does not forward the whole desktop. It forwards only the contents of individual windows, and my Mac's X11 application displays those windows. (The X11 client on my Mac is automatically invoked when necessary.) That I see only individual windows is the problem, although it's not a big one. Since I don't have a Ubuntu desktop while using ssh, I don't have desktop menus, etc., from which to launch GUI apps.

So do you mean that you would rather forward the entire Ubuntu desktop?  That would be easy; just use VNC or NX.  Alternatively, you could forward just the GNOME panel (or the equivalent for whichever desktop environment you prefer on Ubuntu) to your MAC, and launch your Ubuntu applications from there.

---

### Post by brec on 2011-12-21
> **pytheas22 said:**
> So do you mean that you would rather forward the entire Ubuntu desktop?  That would be easy; just use VNC or NX.  Alternatively, you could forward just the GNOME panel (or the equivalent for whichever desktop environment you prefer on Ubuntu) to your MAC, and launch your Ubuntu applications from there.

No, I don't want the whole desktop.  But forwarding just the panel might be good.  How would I do that?

BTW right now I'm using Ubuntu 10.04 with Ubuntu Classic login, i.e., Gnome desktop rather than Unity.

---

### Post by pytheas22 on 2011-12-21
> No, I don't want the whole desktop. But forwarding just the panel might be good. How would I do that?

Easy: just call "gnome-panel" in a terminal session with X11 forwarding enabled on your Mac.

---

### Post by brec on 2011-12-21
> **pytheas22 said:**
> Easy: just call "gnome-panel" in a terminal session with X11 forwarding enabled on your Mac.

Cannot register the panel shell: there is already one running.

[1]+  Exit 255                gnome-panel

---

### Post by pytheas22 on 2011-12-21
Try running with the --replace flag:
```

gnome-panel --replace
```

---

### Post by brec on 2011-12-21
> **pytheas22 said:**
> Try running with the --replace flag:
```

gnome-panel --replace
```

That works.  It also brings a desktop -- a dark purple blank one, as opposed to the background picture on the local system's desktop.  That is of no consequence however.

Because of --replace I thought the local system's panels might disappear, but they remain active.

Would there be a way to dismiss the remote panels, i.e., undo the gnome-panel --replace command without affecting the local system's panels?

---

### Post by pytheas22 on 2011-12-22
> Would there be a way to dismiss the remote panels, i.e., undo the gnome-panel --replace command without affecting the local system's panels?

I'm not sure about that.  But whenever you kill gnome-panel it usually respawns itself automatically, so I would think that if you kill it on the remote session it would regenerate itself locally.  There may also be settings in gconf-editor that would be helpful here for regulating the way gnome-panel behaves.

---

