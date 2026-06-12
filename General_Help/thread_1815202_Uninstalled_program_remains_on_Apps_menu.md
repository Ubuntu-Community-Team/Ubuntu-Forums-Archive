---
title: "Uninstalled program remains on Apps menu"
date: 2011-07-30
forum: General Help
---

### Post by El Judio Bravo on 2011-07-30
I'm not sure how to frame the question; search results get me nothing.

While trying out other web browsers from the 10.10 Software Center I installed Epiphany. I regularly use Firefox 3.6.18 and wanted to see if anything else looked good to me.

I installed and removed Conkeror and Dooble with no problem. I removed Epiphany but to my annoyance, it still appears in my Applications --> Internet menu. I restarted my machine and still it remains there. Click on it and you get a standard "Error" box stating:                  
                                 Could not launch 'Epiphany' 
Failed to execute child process "epiphany-browser" (No such file or directory)

Any ideas what's wrong?

---

### Post by mikewhatever on 2011-07-30
I don't know what's wrong, but instead of trying to figure that out, just open the menu editor and remove that entry. To access the menu editor, right click the menu in the panel, select 'Edit Menu', or System->Preferences->Main Menu.

---

### Post by 73ckn797 on 2011-07-30
Have you tried in terminal:
```
sudo apt-get purge epiphany
``` ?

---

