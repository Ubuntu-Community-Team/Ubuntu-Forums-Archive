---
title: "How to: Edit permissions of /usr folders"
date: 2010-06-06
forum: General Help
---

### Post by rizameister on 2010-06-06
How to copy and overwrite original **bookmarks.adr** file to **/usr/share/opera/default** folder. I can't change permission. Or if is a way to copy it as root ...

---

### Post by pedro_orange on 2010-06-06
You can use cp to copy and chmod to change permissions. Being su helps.
If you want to do it through the GUI you could try opening your file manager as root.

```
sudo nautilus
```

---

### Post by Forged on 2010-06-06
in a terminal

sudo cp file_location new_file_location

---

### Post by rizameister on 2010-06-06
> **pedro_orange said:**
> You can use cp to copy and chmod to change permissions. Being su helps.
If you want to do it through the GUI you could try opening your file manager as root.

```
sudo nautilus
```

> **Forged said:**
> in a terminal

sudo cp file_location new_file_location

Thank you both, that worked

---

