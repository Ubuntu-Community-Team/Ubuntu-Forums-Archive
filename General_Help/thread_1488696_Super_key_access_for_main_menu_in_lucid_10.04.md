---
title: "Super key access for main menu in lucid 10.04"
date: 2010-05-20
forum: General Help
---

### Post by GlennW on 2010-05-20
I noticed that many are looking for the super key to access the main menu. I had this setup in 9.10 but this functionality was lost when doing a fresh 10.04 install. 

Open a terminal and enter this:

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

This website explains it:

[http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html]("http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html")

Have fun!

---

