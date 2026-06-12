---
title: "File Manager Crashes when 20000+ files in single folder."
date: 2010-12-19
forum: General Help
---

### Post by Vigh on 2010-12-19
Hey, 
  just wondering why the file manager, nautilus is it called? can't cope with folders with extremely large numbers of files in it, is there a fix? if not could be a future project for future distributions, i have some folders with 20, 000+ files in it, for rendering fractal animations, i am trying to free up some room, the trash can can't empty it from trash because there are so many files, and when i try to open the folder, it crashes and restarts completely, any help appreciated

regards
ant

---

### Post by tredegar on 2010-12-19
If the GUI crashes, go back to the command line:

rm  -rf  ~/.local/share/Trash/*

Should completely empty the trash for you.

You can also use the command line to manage all those 10,000's of files.

---

