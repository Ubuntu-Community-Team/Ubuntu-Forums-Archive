---
title: "Windows Start Button does not work"
date: 2009-11-05
forum: General Help
---

### Post by ismailkimyacioglu on 2009-11-05
Hi,

I have been using Ubuntu since it was 8.10.  I have made a fresh install of 9.10.  And recently, some buttons or functions do not work.

1. I know how to adjust the windows start to open the main menu.  But in the keyboard shortcuts, when I press on Start button, it doesn't recognize and so I cannot modify it.

2. In mouse settings, I cannot put a tick into the function that Ctrl button will show the location of the pointer with a growing circles.

These all were working in the previous versions.  But although it is a fresh install, they do not now.

By the way, the boot up time seems slower than 9.04.  I don't know everybody has this.

Thanks in advance.

---

### Post by ismailkimyacioglu on 2009-11-26
I have found the solution and wanted to share with you.  In terminal, type gconf-editor.  Under apps, metacity, go to global_keybindings.

Next to "panel_main_menu", under Value section, type "Super_L" and that's it.  Now, Windows start menu will open the panel's main menu.

Still looking for how to initiate the brightness buttons.  Or in other words, I am still looking for how to give brightness up and down commands to buttons.  If you know that please help me.

---

