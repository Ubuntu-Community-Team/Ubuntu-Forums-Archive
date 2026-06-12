---
title: "Can't edit Modules file (/etc directory) to add ath5k"
date: 2009-06-29
forum: General Help
---

### Post by MrCloudHands on 2009-06-29
I need to add the line "ath5k" to my modules file so it will be loaded at boot, however I don't have permissions to save the file after editing it. I know this has something to do with the /etc folder being owned by root, but how can I obtain permission to edit the file? Thanks

---

### Post by Celauran on 2009-06-29
```
sudo vim /etc/modules
```
or
```
gksu gedit /etc/modules
```

---

### Post by kerry_s on 2009-06-29
press **alt+f2**
type>** gksudo gedit /etc/modules**

---

### Post by SuperSonic4 on 2009-06-29
or ```
sudo nano /etc/modules
```

---

### Post by MrCloudHands on 2009-06-29
Problem solved!

I used the gksu gedit command

Thanks for the help

---

