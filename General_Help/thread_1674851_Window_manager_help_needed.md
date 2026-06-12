---
title: "Window manager help needed"
date: 2011-01-24
forum: General Help
---

### Post by Mokolodi1 on 2011-01-24
So a few days ago I installed the Compiz window manager. I've been having some trouble getting my title bar (the bar on the top of the window which has the close, maximize, minimize buttons on it). I know that I need to change my Window Decorator to GTK, but can't figure out how to do that. I can change it in the settings, but nothing happens when I do so. Thank you in advance for any advice!

---

### Post by Frogs Hair on 2011-01-24
I don't know what settings you have changed but try this in the terminal.```
metacity ~~replace
```

---

### Post by lightningfox on 2011-01-24
Install fusion-icon. It lets you easily switch between window decorators and managers.

---

### Post by Mokolodi1 on 2011-01-24
As far as I can tell, Metacity does not support a 3D desktop which I really like. I have Fusion-icon installed already but it only has one option for window decoration, KDE4. Is it possible to keep Compiz but have GTK as my window decoration?

---

### Post by MichaelGld on 2011-01-24
> **lightningfox said:**
> Install fusion-icon. It lets you easily switch between window decorators and managers.

I installed the fusion icon. The first time I ran it, my desktop icons temporarily disappeared. Subsequently, when I ran it, nothing noticeable happened at all. Thinking my install might have been corrupted, I removed and reinstalled it through the Software Center. Nothing changed, I don't see anything changing when I run it.

Thanks.

---

### Post by Krytarik on 2011-01-24
I don't know how fusion-icon works or what options it has.

If you want to revert to the default window decorator, press Alt+F2 and enter this:
```
gtk-window-decorator --replace
```

I don't know how to change which window decorator is run by default at startup, maybe by entering it here: "System -> CompizConfig Settings Manager -> Window Decoration -> Command". Did you mean that?

If you changed it there, Compiz has to be restartet to put it into affect:
```
compiz --replace
```

---

### Post by Mokolodi1 on 2011-01-24
I've tried both of your recommended methods to no avail. Attached is a screenshot of what I get for the first one.

---

### Post by Krytarik on 2011-01-24
Interesting, your PATH variables seem to be corrupted:
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

Try the full path then:
```
/usr/bin/gtk-window-decorator --replace
```

Could someone give a quick and precise hint regarding PATH?

---

