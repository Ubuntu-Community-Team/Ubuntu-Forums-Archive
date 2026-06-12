---
title: "GUI changes when I sudo a GUI'd application."
date: 2006-05-28
forum: General Help
---

### Post by Plank117 on 2006-05-28
This isn't really a functionality problem, but it's still pretty annoying. Whenever I run, say, OpenOffice Writer with sudo it opens up with this exceptionally fugly GUI instead of the custom GUI I had gotten off of gnome-look. Why is this, and is there any way to fix it? It's really been getting on my nerves lately.

---

### Post by 23meg on 2006-05-28
[QUOTE=Plank117]This isn't really a functionality problem, but it's still pretty annoying. Whenever I run, say, OpenOffice Writer with sudo it opens up with this exceptionally fugly GUI instead of the custom GUI I had gotten off of gnome-look. Why is this, and is there any way to fix it? It's really been getting on my nerves lately.[/QUOTE]
Run gnome-theme-manager as root and choose a root theme. To make themes available for choosing put them in /usr/share/themes

---

### Post by Plank117 on 2006-05-28
Spiffy. Thanks.

---

### Post by mcduck on 2006-05-29
[QUOTE=Plank117]Spiffy. Thanks.[/QUOTE]
Or, if you want apps run as root to have same theme that you have, do this:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
(sudo ln -s ~/.fonts /root/.fonts)
```

By the way, I suppose running OO Writer with sudo was just an example, as I can't think of any sane reason to do such thing :rolleyes:

---

