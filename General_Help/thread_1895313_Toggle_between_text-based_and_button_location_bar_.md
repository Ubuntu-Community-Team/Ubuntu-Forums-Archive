---
title: "Toggle between text-based and button location bar (Oneiric)"
date: 2011-12-14
forum: General Help
---

### Post by ricardo06 on 2011-12-14
Hello, since I upgraded to 11.10, Nautilus 2.3.1 opens with a text based location bar. I tried CTRL-L to switch back to button based, but all that CTRL-L does is that it selects the path in the location bar. 
I tried to change the settings in the gconf editor but it just does nothing.
can anybody help please.
Thanks a lot in advance.

Richard

---

### Post by seawolf167 on 2011-12-14
What did you change in gconf-editor?

To change to text from buttons you edit:

Hit [ALT][F2], then enter
```
gconf-editor
```

then check the box by
```
/apps/nautilus/preferences/always_use_location_entry
```

To change back just remove the check box.

Have you tried logging out and logging back in?

---

### Post by ricardo06 on 2011-12-14
Thanks a lot for your fast answer. 
The modification you propose does not change nautilus behavior.
Even after loging out and back in.

Richard

---

### Post by seawolf167 on 2011-12-14
Sorry, I totally forgot that 11.10 uses dconf-editor. Try changing the setting there

```
sudo apt-get install dconf-tools
```

```
[ALT][F2]
dconf-editor
```

The location is
```
org/gnome/nautilus/preferences/always-use-location-entry
```

Let me know if that works.

---

### Post by ricardo06 on 2011-12-14
Just Great
Thanks a lot
Richard

---

### Post by seawolf167 on 2011-12-14
If it worked, please mark this thread as solved

---

