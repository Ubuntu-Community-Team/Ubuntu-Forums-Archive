---
title: "gtk theme and synaptics in openbox"
date: 2010-07-16
forum: General Help
---

### Post by launchy on 2010-07-16
how do i apply the gtk theme elementary to synaptic package manager in openbox? i have selected it in lxappearance and the elementary folder is in /usr/share/themes and ~/.themes.

---

### Post by launchy on 2010-07-18
--bump--

---

### Post by launchy on 2010-07-19
__bump__

---

### Post by launchy on 2010-07-21
^ anyone?

---

### Post by urukrama on 2010-07-22
You have to set the theme in your /root/.gtkrc-2.0 file (which you could do manually or by running LXAppearance as root). 

If you want that file to be updated whenever you update your (non-root) Gtk theme, you link that file to your ~/.gtkrc-2.0 file:

```
sudo ln ~/.gtkrc-2.0 /root/.gtkrc-2.0
```

---

### Post by launchy on 2010-07-22
wow thank you again!! ive never thought of running lxappearance as root. that worked! :-D

---

