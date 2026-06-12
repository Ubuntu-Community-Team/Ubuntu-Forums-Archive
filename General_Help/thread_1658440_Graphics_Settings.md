---
title: "Graphics Settings"
date: 2011-01-02
forum: General Help
---

### Post by augdawg09 on 2011-01-02
Hey all,

A few days back, I was playing around in the Appearance preferences (or CompizConfig or something) and somehow something got messed up. The graphics level went back to the "None" setting. I thought that this would be okay because then I could just go back to the Appearance preferences and change it back to the "Normal" setting. When I tried this, it created a pop-up window that said "Searching for Drivers." Then, my desktop started flickering (all of the windows started disappearing and then reappearing).

Does anyone know how I can fix this so that the settings are back on the "Normal" setting?

Thanks in advance!

:popcorn:

---

### Post by wojox on 2011-01-02
What graphics card/chipset do you have:

```
lspci | grep VGA
```

---

### Post by augdawg09 on 2011-01-02
The output:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

---

### Post by wojox on 2011-01-02
What if you run:

```
compiz --replace
```

---

### Post by augdawg09 on 2011-01-02
It appears that did the trick! :p

Should I just have "compiz --replace" run on startup?

---

### Post by wojox on 2011-01-02
Open a terminal and run

```
sudo gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager compiz
```

This should set your Window Manager to Compiz.

---

### Post by augdawg09 on 2011-01-03
Thanks for your help!

---

