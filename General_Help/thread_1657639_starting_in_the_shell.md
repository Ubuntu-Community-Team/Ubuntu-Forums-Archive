---
title: "starting in the shell"
date: 2011-01-01
forum: General Help
---

### Post by Garrett85 on 2011-01-01
How can I start up my Ubuntu Linux in the shell? Then how could I make sure to also get back to gnome?

---

### Post by sisco311 on 2011-01-01
Edit the file /etc/default/grub. Replace the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** with **GRUB_CMDLINE_LINUX_DEFAULT="text"** then generate a new Grub2 config file:
```
sudo update-grub
```

To start an X session run:
```
startx
```

---

