---
title: "Restoring Pannels in Ubuntu 10.04"
date: 2010-08-27
forum: General Help
---

### Post by trunkmonkeytoo on 2010-08-27
My panels in Ubuntu have changed appearance, and I can't figure out how to put them back to the default settings in 10.04, and I can't use my widgets, like Evolution. How do you restore them to the default settings? 

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6684[/IMG]

---

### Post by sisco311 on 2010-08-27
Open a terminal and run:
```
gconftool-2 --recursive-unset /apps/panel
```and
```
killall gnome-panel
```

---

### Post by trunkmonkeytoo on 2010-08-27
That took the panel away, and and brought it back with the second code, but it still looks the same, and I don't have the bottom panel, still. Is there anything else I could try?

---

### Post by wojox on 2010-08-27
That should have worked. [Try this]("http://ubuntuforums.org/showpost.php?p=9245108&postcount=3")

---

### Post by trunkmonkeytoo on 2010-08-27
That had the same effect after I put in pkill gnome-panel, it took the panel away, and replaced it with the same one. :(

---

### Post by 13east on 2010-08-27
> **trunkmonkeytoo said:**
> My panels in Ubuntu have changed appearance, and I can't figure out how to put them back to the default settings in 10.04, and I can't use my widgets, like Evolution. How do you restore them to the default settings? 

[IMG]http://ubuntuforums.org/picture.php?albumid=1992&pictureid=6684[/IMG]

-right click on a panel -> add to panel:
everything that was once there should be here as well
(i.e. indicator for volume&evolution and notification icons)

---

### Post by trunkmonkeytoo on 2010-08-27
> **13east said:**
> -right click on a panel -> add to panel:
everything that was once there should be here as well
(i.e. indicator for volume&evolution and notification icons)

Hey thanks! That worked! I added all of the apps that I had on the top and bottom panels.:p

---

