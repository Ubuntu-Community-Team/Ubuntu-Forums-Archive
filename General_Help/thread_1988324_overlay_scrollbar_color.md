---
title: "overlay scrollbar color"
date: 2012-05-27
forum: General Help
---

### Post by vasa1 on 2012-05-27
In Ubuntu 12.04, by editing **/usr/share/themes/Ambiance/gtk-3.0/gtk-widgets.css**, I can change the color of the overlay scrollbar:
```
/* overlay scrollbar */
OsThumb {
    color: shade (#f07746, 1.6);
}

OsThumb:selected,
OsScrollbar:selected {
    background-color: #f07746;
}

OsThumb:active,
OsScrollbar:active {
    background-color: shade (#f07746, 0.6);
}

OsThumb:insensitive,
OsScrollbar:insensitive {
    background-color: shade (#f07746, 0.85);
}


```

My question is this: how can I do the same for gtk-2.0 apps?

---

### Post by vasa1 on 2012-05-27
This how I did it:

In my /usr/share/themes/Ambiance/gtk-2.0/gtkrc, the first section has ```
gtk-color-scheme = "base_color:#555555\nfg_color:black\ntooltip_fg_color:#4974a7\nselected_bg_color:#003263\nselected_fg_color:maroon\ntext_color:black\nbg_color:#555555\ntooltip_bg_color:#000000\nlink_color:#f07746"

```
Further down, we have:```
style "overlay_scrollbar"
{
	bg[SELECTED] = shade (1.0, @selected_bg_color)
	bg[INSENSITIVE] = shade (0.85, @bg_color)
	bg[ACTIVE] = shade (0.6, @bg_color)
}

```
Instead of *selected_bg_color* and *bg_color*, use any thing from the first section. I used *link_color*.

---

