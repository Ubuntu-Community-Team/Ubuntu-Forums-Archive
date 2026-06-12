---
title: "How to change some colors in Ambiance theme ?"
date: 2012-06-08
forum: General Help
---

### Post by rostom_zer on 2012-06-08
hello

i wanna change that orange color in the Ambiance theme

as you know, we can see the orange color in nautilus selected item for example

or focused item in dropdown menus ets...

got it ?

how to change the color value please ?

thanX...

---

### Post by mc4man on 2012-06-08
There is a user override in dconf (dconf-editor) that you can use to alter the common color defines
In the case of the orange it's selected_bg_color
Many times if changing that you may also want to change the text in the selected to better match, so that would be selected_fg_color

To set in dconf-editor you click in the 'value' area till it turns white, (screen 2),  type in whatever, then press enter on the keyboard. Don't click out of the edit box or the setting won't take

Screens show how to enter, more than one entry is separated by a ;

Alternately you can use gsettings, so command for what was in the screen would be, (basically same as using dconf-editor except enclosed in ""

```
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_bg_color:#D3B37D;selected_fg_color:#3c3b37"

```

Fool around till you get what you like, to reset just click on "Set to Default" when key is highlighted in dconf-editor or from cli
```
gsettings set org.gnome.desktop.interface gtk-color-scheme ""
```

---

### Post by rostom_zer on 2012-06-09
Got it !

thanX for helping...

---

### Post by MartinRuthenberg on 2013-01-18
I'd like to change colors in Radiance Theme of Ubuntu 12.04. But dconf-editor doesn't have those options any more. What else can I do?

Thanks
Martin

---

