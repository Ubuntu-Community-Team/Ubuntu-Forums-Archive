---
title: "Making Nautilus display the desktop again"
date: 2010-05-12
forum: General Help
---

### Post by warnec on 2010-05-12
So I've used gconf-editor to disable the "show_desktop" feature of Nautilus to get multiple wallpapers to work, but now want my icons back. But I can't:
```

warnec@lucidL:~$ LANG=C sudo gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
Error setting value: Can't overwrite existing read-only value: Value for `/apps/nautilus/preferences/show_desktop' set in a read-only source at the front of your configuration path

```

Any idea? It does neither work with gconf-editor. It says this key is "protected from writing"

---

### Post by ankspo71 on 2010-05-12
I'm not sure, but try without sudo, because it might be trying to change the root users gnome preferences. From what I read here, launching gconf-editor with sudo will make changes to root.
Hope this helps.

---

### Post by warnec on 2010-05-12
Nope, still no go.
```

warnec@lucidL:~$ LANG=C gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
Error setting value: Can't overwrite existing read-only value: Nie mo?na nadpisa? istniej?cej warto?ci przeznaczonej tylko do odczytu: Warto?? "/apps/nautilus/preferences/show_desktop" jest ustawiona w ?r?dle tylko od odczytu na pocz?tku ?cie?ki konfiguracji

```

Same error, only in Polish now.

---

### Post by warnec on 2010-05-13
I fixed it by selecting "Clear the key" option (or similar, my sytsem is Polish) in gconf-editor. Now I have my icons back, yay!

---

