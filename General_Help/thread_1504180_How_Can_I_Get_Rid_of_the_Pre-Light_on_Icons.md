---
title: "How Can I Get Rid of the Pre-Light on Icons?"
date: 2010-06-07
forum: General Help
---

### Post by Joseph Schwenker on 2010-06-07
I am using Ubuntu 10.04 with 9.10's Humanity icon theme.  I have been irritated for a long time about the prelight on icons.  That is, how icons light up when you hover over then in any view except list view.  How can I get rid of the prelight?

---

### Post by Joseph Schwenker on 2010-06-15
I am now using Elementary.  How can I remove the prelight from icons and buttons?

---

### Post by Joseph Schwenker on 2010-06-17
bump

---

### Post by Joseph Schwenker on 2010-06-21
bump

---

### Post by Joseph Schwenker on 2010-07-04
bump

---

### Post by Joseph Schwenker on 2010-08-04
bumpity, bumpity, bump

---

### Post by Vaphell on 2010-08-04
probably you need to hack few files in /usr/share/themes/<your_theme>, most probably gtkrc in gtk-2.0 subdir. there is a lot of stuff like

```
style "button" = "selected"
{
	bg[NORMAL]   = shade (0.9, @selected_bg_color)
	bg[PRELIGHT] = shade (1.0, @selected_bg_color)
	bg[SELECTED] = shade (1.0, @selected_bg_color)
	bg[ACTIVE]   = shade (0.9, @selected_bg_color)
	bg[INSENSITIVE]   = mix (0.3, @selected_bg_color, @bg_color)
```

it looks quite hardcore though

---

### Post by Joseph Schwenker on 2010-08-04
> **Vaphell said:**
> probably you need to hack few files in /usr/share/themes/<your_theme>, most probably gtkrc in gtk-2.0 subdir. there is a lot of stuff like

```
style "button" = "selected"
{
	bg[NORMAL]   = shade (0.9, @selected_bg_color)
	bg[PRELIGHT] = shade (1.0, @selected_bg_color)
	bg[SELECTED] = shade (1.0, @selected_bg_color)
	bg[ACTIVE]   = shade (0.9, @selected_bg_color)
	bg[INSENSITIVE]   = mix (0.3, @selected_bg_color, @bg_color)
```

it looks quite hardcore though

Thanks, I'll try that.

Edit: I did a search for "prelight" in Gedit and deleted all entries present for prelight, but nothing was largely affected besides button prelight changing from blue to a light brown gradient.

---

### Post by Vaphell on 2010-08-04
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes/StyleProperties#NautilusIconContainer](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes/StyleProperties#NautilusIconContainer)

these are nautilus specific parameters and it looks like they are able to control the icon highlights but i have no idea how to add them properly to the theme. I am not motivated enough to find out :-)

---

### Post by Joseph Schwenker on 2010-08-11
bump

---

