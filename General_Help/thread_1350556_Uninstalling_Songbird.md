---
title: "Uninstalling Songbird"
date: 2009-12-09
forum: General Help
---

### Post by mesbah_1242 on 2009-12-09
I've installed songbird by executing a .deb file. the launcher is in Applications->Sound & video  category. I want to uninstall it but i can not find it in my add/remove panel or in synaptic pakage manager. the main site says to delete the folders named songbird but those folders have a lock mark on them and i can not delete them. anyone can explain how to remove songbird completely from my computer?

---

### Post by khelben1979 on 2009-12-09
Open up a graphical file manager with super user priviliges (root). From there you can delete the directory containing Songbird.

---

### Post by sisco311 on 2009-12-09
> **mesbah_1242 said:**
> I've installed songbird by executing a .deb file. the launcher is in Applications->Sound & video  category. I want to uninstall it but i can not find it in my add/remove panel or in synaptic pakage manager. the main site says to delete the folders named songbird but those folders have a lock mark on them and i can not delete them. anyone can explain how to remove songbird completely from my computer?

Open a terminal (Applications -> Accessories -> Terminal)
and run:
```
sudo apt-get remove songbird
```

In Synaptic, songbird should be in the *audio* section (screenshot attached).

---

### Post by mesbah_1242 on 2009-12-12
i've deleted the files using sudo command.
thank you guys.

---

