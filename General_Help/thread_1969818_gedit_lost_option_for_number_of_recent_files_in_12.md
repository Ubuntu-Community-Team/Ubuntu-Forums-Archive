---
title: "gedit lost option for number of recent files in 12.04"
date: 2012-04-30
forum: General Help
---

### Post by Paddy Landau on 2012-04-30
Fresh installation of 12.04 (fully updated).

In the old gedit (I had 11.04), I was able to adjust the number of recent files listed; 5 was too few for me, and 10 was about right.

The method was gconf-editor > /apps/gedit-2/preferences/ui/recents > max_recents.

However, the new gedit is missing that option.

Any idea how to increase the number of recent files listed in gedit?

---

### Post by stinkeye on 2012-04-30
A lot of settings are now in dconf.
You can use dconf-editor in the dconf-tools package

or

Terminal command...
```
gsettings set org.gnome.gedit.preferences.ui max-recents 10
```

---

### Post by Paddy Landau on 2012-05-01
> **stinkeye said:**
> ```
gsettings set org.gnome.gedit.preferences.ui max-recents 10
```
That worked, thank you.

The command created a value of zero for some reason, so I had to enter gconf-editor to change it to 10. But at least I know how to create the value now.

---

