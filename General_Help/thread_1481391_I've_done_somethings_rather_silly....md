---
title: "I've done somethings rather silly..."
date: 2010-05-12
forum: General Help
---

### Post by Trilby on 2010-05-12
On a website about Ubuntu I found, I saw a terminal command to make the super (windows) key open the applications menu, like win key does with windows' start menu. On the spur of the moment I thought, "that sounds useful", and copied it into terminal. Now none of my keyboard shortcuts involving super key work and I don't know how to undo what I did. The command I found is as follows:
```
gconftool-2 --set  /apps/metacity/global_keybindings/panel_main_menu --type string  "Super_L"
```I found it at [http://wojox.homelinux.org/](http://wojox.homelinux.org/)

Can anyone help? I feel a bit daft.

Thanks,
Trilby.

---

### Post by plucky on 2010-05-12
To reset it ```
gconftool-2 --set  /apps/metacity/global_keybindings/panel_main_menu --type string  "<Alt>F1"
```

Or in a terminal ```
gconf-editor
``` and then navigate to **apps > metacity > global_keybindings > panel_main_menu** and change "Super_L" to "<Alt>F1"

Good Luck

---

### Post by Trilby on 2010-05-12
Thank you.
(I used the first suggestion).
I will be more careful in future :redface:

---

### Post by wojox on 2010-05-12
I reposted to your comment you know. :)

---

### Post by Trilby on 2010-05-14
> **wojox said:**
> I reposted to your comment you know. :)

Ha, well, that'll be the last time I do anything you suggest :lolflag:

---

