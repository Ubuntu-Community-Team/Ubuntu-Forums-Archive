---
title: "disable F10: gconftool vs. .gtkrc-2.0"
date: 2010-11-06
forum: General Help
---

### Post by chrisstankevitz on 2010-11-06
F10 makes the "File" menu open.  According to Google, either of these two methods should disable this behavior:

Method 1:
```
gconftool-2 --type string --set /desktop/gnome/interface/menubar_accel ""
```

Method 2:
```
echo "gtk-menu-bar-accel = \"\"" >> ~/.gtkrc-2.0
```

For me, only Method 1 works.  I have two questions:

1. Why doesn't Method 2 work?

2. How can I get the Method 1 instruction to run automatically every time I start gnome?

Thank you,

Chris

---

