---
title: "The common Error"
date: 2010-09-14
forum: General Help
---

### Post by abdusamed on 2010-09-14
Lately, I'm facing crashes throughout my system regularly on the same apps even after updating/reinstalling. I thing it's a common error which can be fixed my recompiling or doing something. I think it's to do with X display or something from reading the logs in the terminal after running the application.

Below are the tested programs with logs

Cheese
```

The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 80 error_code 8 request_code 133 minor_code 19)

```
Miro
```

The program 'miro.real' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7983 error_code 8 request_code 1 minor_code 0)

```

Avidmux
```

Resize plugin not found

```

Kaffine
```

bahie@bahie-laptop:~$ kaffeine

progname=<unknown>; RGBA=on

progname=<unknown>; RGBA=on
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
bahie@bahie-laptop:~$ QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/bahie/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kaffeine(2614)/kio (KDirModel) KDirModelPrivate::_k_slotDeleteItems: No node found for item that was just removed: KUrl("file:///home/bahie/Documents/dolphin-20100901-055035.kcrash") 

(<unknown>:2636): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(<unknown>:2614): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

```
Geany
```

bahie@bahie-laptop:~$ geany 

progname=geany; RGBA=on
Segmentation fault

```

Also, I'm using VDPAU version of mplayer if that helps.

---

### Post by stinkeye on 2010-09-15
Some or all of your problems may be due to using RGBA.
Some programs don't play nicely with RGBA.

You can blacklist programs from using RGBA by
```
gedit ~/.profile &
```


and add to the very bottom
```
export GTK_MODULES=rgba
export GTK_RGBA_APPS=allbut:firefox-bin:gnome-mplayer:totem:soffice
```
You can blacklist more programs by adding a **:** followed by the program name.
Use system monitor to get the correct name.

---

### Post by abdusamed on 2010-09-15
anyway of disabling RGBA all together? I remember doing loads of searching only to make gnome panel transparent! I regret trying to do so.

Also, I think this is normal message because i've been reading this whenever any programs ends in terminal and doesn't seem to do change anything but is it actually 'normal'?

```

(gedit:29979): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:29979): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:29979): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed


```

---

### Post by stinkeye on 2010-09-15
I installed RGBA using the method described in this blog.
Down the bottom it says how to revert the changes.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html[/COLOR]_**]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html")

Did you find out how to get your panel transparent without having a background image to some of your applets?

---

### Post by abdusamed on 2010-09-16
well that didn't work for me.. I don't even have the ppa and I forgot I enabled murrine but from the method it describes, I remember doing something very close to it. Some how i need to uninstall RGBA altogether

---

### Post by abdusamed on 2010-09-17
In the profile gedit file, what should I put which would say, don't run rgba on anything instead of simply exclusion apps? 

Will 'false' or 'none' work instead of 'allbut'? I'm asking because I don't be left with no desktop if I reboot my desktop!

---

### Post by stinkeye on 2010-09-17
Don't know, but if you leave out the allbut you can run it just for particular applications
eg...
GTK_RGBA_APPS=gedit
will make RGBA only work with gedit.

---

### Post by abdusamed on 2010-09-18
> **stinkeye said:**
> Don't know, but if you leave out the allbut you can run it just for particular applications
eg...
GTK_RGBA_APPS=gedit
will make RGBA only work with gedit.

Thanks, that works.. finally I don't see any RGBA error

---

### Post by abdusamed on 2010-10-01
Okay,, found the solution.. it had to do with gnome2 panel and rgba... thanx


Uninstalling both fixed my pc

---

### Post by ytim on 2011-01-16
Hi Amusamed,

Just to be on the safe side because I don't want to assume... are you saying that all you did was uninstall gnome2 panel and rgba?  Would you mind being a bit more specific with your solution please?  It would help us n00bs alot!  :)

ytim@pgos:~$ cd /root ; gedit .bashrc
bash: cd: /root: Permission denied

(gedit:12508): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
(gedit:12508): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
(gedit:12508): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

Thx again.
YTim

> **abdusamed said:**
> Okay,, found the solution.. it had to do with gnome2 panel and rgba... thanx


Uninstalling both fixed my pc

---

### Post by abdusamed on 2011-01-17
i'm no pro at ubuntu

the global menu applet was what i was referring to when i said 'gnome2panle'

---

