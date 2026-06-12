---
title: "Graphics card help..."
date: 2009-10-11
forum: General Help
---

### Post by letmekilluplz on 2009-10-11
I have a fairly old computer in which they don't make drivers for anymore.. at least none are available on the ATI website. I can't watch youtube or anything flash could it be because I don't have graphics drivers? 

I'm not extremely skilled with computers so sorry if this is a stupid question. 

PS. Spoonfed if possible:confused:

---

### Post by ajgreeny on 2009-10-11
Lack of flash videos is probably nothing to do with drivers; if you have a gnome desktop (or kde or xfce, depending on your choice) then you have drivers for the graphics card already installed.

You now need to enable all the repositories in System ->Administration -> Software Sources and install adobe-flashplugin.  Job done.

---

### Post by tuxxy on 2009-10-11
The package required is flashplugin-nonfree, search for it using Synaptic or enter in terminal;

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by ajgreeny on 2009-10-12
Don't worry too much about which of these two answers to use.  Both ways end up in more or less the same place, with a working **libflashplayer.so** in one of the plugin folders of your system.

---

