---
title: "Missing icons"
date: 2011-12-01
forum: General Help
---

### Post by ully-mick on 2011-12-01
Ubuntu 11.10 running G3 fallback. everythings running fine including compiz, apart from volume icon missing and network connection missing from notification area.
if I run "gnome-volume-control-applet" I get this error message - Could not open location 'file:///home/mick/gnome-volume-control-applet'

Error stating file '/home/mick/gnome-volume-control-applet': No such file or directory

the network connection is there, just no icon. if I mouse over I get the network status.

I uninstalled Banshee because I don't use it, I use Audacious. any ideas?

---

### Post by BC59 on 2011-12-01
The problem with Gnome 3, Gnome-shell and fallback is that Canonical doesn't not provide full support.

Look if it's working better if you reinstall it:

```
sudo apt-get install --reinstall gnome-session-fallback
```

```
sudo apt-get install --reinstall gnome-shell
```

---

### Post by ully-mick on 2011-12-02
thanks for the help.
reinstall gnome-session-fallback fixed the icon but broke compiz. fixing compiz lost the icon again :)

it must be a compiz bug. I think I'll stick with what I've got.

thanks again for trying,

---

### Post by BC59 on 2011-12-02
You can reset Compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

It's a little long command, but it's working.

---

