---
title: "Change desktop icon text color in 11.10\12.04"
date: 2012-01-15
forum: General Help
---

### Post by TheNessus on 2012-01-15
how?


thank you

---

### Post by lechien73 on 2012-01-15
I don't think this can be done through dconf, or Compiz, but I remember reading that if you open a terminal window and type:

```
gksu gedit /usr/share/themes/Ambiance/gtk-3.0/apps/nautilus.css
```

You can edit the settings in the "desktop mode" section.

@bg_color is the color of the icon text when not selected
@fg_color is the color of the icon text when double-clicked
@selected_fg_is the color of the icon text when selected

You can use hex colour codes, or standard colour names such as red, blue, yellow etc.

You probably have to log out and in again for this to take effect.

---

### Post by vasa1 on 2012-01-15
I had answered a slightly longer question over [here]("http://askubuntu.com/questions/89734/how-can-i-change-the-text-colour-on-my-desktop-icons/89929#89929") but there's no knowing if the questioner ever came back :D
Anyway, as pointed out above by lechien73:> 
@bg_color is the color of the icon text when not selected
@fg_color is the color of the icon text when double-clicked
@selected_fg_is the color of the icon text when selected
though I feel that **fg_color** can affect more than one desktop icon "state" but I don't know the correct terms.

---

### Post by TheNessus on 2012-01-16
thanks for the answers. But won't that change the color only in "Ambiance" theme? I don't like Ambiance, I'm using custom one.

---

### Post by vasa1 on 2012-01-16
> **TheNessus said:**
> thanks for the answers. But won't that change the color only in "Ambiance" theme? I don't like Ambiance, I'm using custom one.
Does that one have a nautilus.css? Edit that one?

---

