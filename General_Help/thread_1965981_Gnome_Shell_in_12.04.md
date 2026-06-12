---
title: "Gnome Shell in 12.04"
date: 2012-04-26
forum: General Help
---

### Post by merlinus on 2012-04-26
Is there a way to get Classic Gnome or Gnome Shell, as in 11.10, or will I have to install xubuntu or LinuxMint in order to get rid of unity?

---

### Post by wojox on 2012-04-26
There is a package for both:
```
sudo apt-get install gnome-shell
```

```
sudo apt-get install gnome-session-fallback
```

---

### Post by Eirreann on 2012-04-26
> **wojox said:**
> There is a package for both:
```
sudo apt-get install gnome-shell
``````
sudo apt-get install gnome-session-fallback
```

These install as separate packages that I access from the login screen, right?  I don't want to overwrite Ubuntu, but I'd like to not have to deal with Unity (it's buggy with the new update)

---

### Post by merlinus on 2012-04-26
Once the packages are installed, yes, you can choose them from the login screen.  And I am very glad not to be forced to use unity in 12.04!!!

---

### Post by wojox on 2012-04-26
> **Eirreann said:**
> These install as separate packages that I access from the login screen, right?  I don't want to overwrite Ubuntu, but I'd like to not have to deal with Unity (it's buggy with the new update)

Of course. You will have an array of choices when you reboot. :D

---

### Post by sgage on 2012-04-26
> **Eirreann said:**
> These install as separate packages that I access from the login screen, right?  I don't want to overwrite Ubuntu, but I'd like to not have to deal with Unity (it's buggy with the new update)

If you install gnome-shell, it will also bring in "Gnome Classic" (gnome-fallback-session). Yes, you will then have the new options in your login screen:

Gnome = Gnome Shell
Gnome Classic = the fallback UI (looks like good ol' 2-panel Gnome, with Compiz)
Gnome Classic (No Effects) = the fallback UI with straight up Metacity

---

