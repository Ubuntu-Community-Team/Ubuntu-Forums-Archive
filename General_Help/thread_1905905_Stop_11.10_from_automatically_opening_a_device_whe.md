---
title: "Stop 11.10 from automatically opening a device when I plug it in?"
date: 2012-01-07
forum: General Help
---

### Post by josephellengar on 2012-01-07
11.10, gnome 3
Whenever I plug in a flash drive or other external storage media, a nautilus window is automatically opened to the root of this device. Is there a way to modify this behavior? I couldn't find it in the nautilus preferences. Maybe a gconf/dconf key?

---

### Post by bluexrider on 2012-01-07
**Configuring Automounting**

 To enable or disable automount open a terminal and type **gconf-editor** followed by the **[Enter]** key. 
Browse to **/apps/nautilus/preferences/media_automount**.

after whatever changes are made then       ```
nautilus -q
```




[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by josephellengar on 2012-01-08
> **bluexrider said:**
> **Configuring Automounting**

 To enable or disable automount open a terminal and type **gconf-editor** followed by the **[Enter]** key. 
Browse to **/apps/nautilus/preferences/media_automount**.

after whatever changes are made then       ```
nautilus -q
```




[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

No good. That information is old. The preferences key is no longer there and there is no corresponding key in dconf. Also, I'm not trying to prevent it from automounting. I'm trying to prevent it from automatically opening a window *after* automounting. You're probably looking at information for gnome 2.

---

### Post by josephellengar on 2012-01-09
bump

---

### Post by silverhaze06 on 2012-01-09
> **josephellengar said:**
> No good. That information is old. The preferences key is no longer there and there is no corresponding key in dconf. Also, I'm not trying to prevent it from automounting. I'm trying to prevent it from automatically opening a window *after* automounting. You're probably looking at information for gnome 2.I would also like to know how to do this. Anybody know how?

---

### Post by pr3zident on 2012-01-09
go to removable media and edit the settings ....

---

### Post by josephellengar on 2012-01-09
> **pr3zident said:**
> go to removable media and edit the settings ....

Thanks!

---

### Post by pr3zident on 2012-01-09
> **josephellengar said:**
> Thanks!

No problem

---

