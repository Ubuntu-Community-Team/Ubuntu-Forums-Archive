---
title: "So, what happened to the themes in 12.04?"
date: 2012-05-23
forum: General Help
---

### Post by Tamalin on 2012-05-23
I have recently upgraded to Ubuntu 12.04 and I wondered where all the themes went!

I can still:
```

$ ls /usr/share/themes
AgingGorilla  Clearlooks  Esco                 LowContrast  Raleigh
Ambiance      Crux        HighContrast         Metabox      Redmond
Atlanta       Default     HighContrastInverse  Mist         Simple
Bright        Emacs       Industrial           Radiance     ThinIce

```

But only four of these are available in system preferences.  Can I get the others back?

---

### Post by roelforg on 2012-05-23
Same on my 11.10 machine

---

### Post by MG&amp;TL on 2012-05-23
Although it (annoyingly) installls gnome-shell as a dependency, you can use those themes:

```
sudo apt-get install gnome-tweak-tool
```

...then look for 'advanced settings'.

---

### Post by Tamalin on 2012-05-23
So can I not use or install any themes other than the default four without installing gnome-tweak-tool?  Maybe I can use gconf-editor?

---

### Post by stinkeye on 2012-05-23
Have a look at myunity.
[http://www.omgubuntu.co.uk/2012/02/unity-tweaking-tool-gets-new-look-new-features/]("http://www.omgubuntu.co.uk/2012/02/unity-tweaking-tool-gets-new-look-new-features/")

---

### Post by diesch on 2012-05-23
Use MyUnity from Software Center or [Unsettings]("http://www.florian-diesch.de/software/unsettings") to change the themes with a GUI.

On the command line you can use

```
settings set org.gnome.desktop.interface gtk-theme some_gtk-theme
```
and
```
gsettings set org.gnome.desktop.wm.preferences theme some_metacity_theme
```

Or use *dconf-editor* (package *dconf-tools*) to modify this keys.

---

### Post by Tamalin on 2012-05-23
> **stinkeye said:**
> Have a look at myunity.
[http://www.omgubuntu.co.uk/2012/02/unity-tweaking-tool-gets-new-look-new-features/]("http://www.omgubuntu.co.uk/2012/02/unity-tweaking-tool-gets-new-look-new-features/")

I like this.  I'm still surprised there isn't really any built-in way to handle this sort of thing, but at least it's still possible.

EDIT:
I didn't see diesch's post.  This is sort of what I was looking for in the first place.  I always prefer to avoid third party software for "system functions" if possible.

---

### Post by MadmanRB on 2012-05-23
You should try ubuntu tweak too, its third party software yes but its very good software non the less.

---

