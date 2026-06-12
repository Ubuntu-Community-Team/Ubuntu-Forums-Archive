---
title: "'Pictures' disappeared from the 'Places' menu"
date: 2011-08-29
forum: General Help
---

### Post by Tornikee on 2011-08-29
Hello, I have this minor issue for 11.04 - 'Pictures' is no longer shown among the 'Documents', 'Videos' and other folder shortcuts in the 'Places' menu of the panel. The Pictures folder itself is present among those, but the shortcut has disappeared. How can it be restored/added to the menu?

---

### Post by scott_g on 2011-08-29
I haven't used 11.04 yet, but have you tried opening the folder in the file manager, and dragging the folder to the shortcut menu?

Scott

---

### Post by Slim Odds on 2011-08-29
> **scott_g said:**
> I haven't used 11.04 yet, but have you tried opening the folder in the file manager, and dragging the folder to the shortcut menu?

Scott

Go to any folder that you like and use Menu->Bookmarks->Add Bookmark

---

### Post by mcduck on 2011-08-30
> **Tornikee said:**
> Hello, I have this minor issue for 11.04 - 'Pictures' is no longer shown among the 'Documents', 'Videos' and other folder shortcuts in the 'Places' menu of the panel. The Pictures folder itself is present among those, but the shortcut has disappeared. How can it be restored/added to the menu?

Didi you at any point accidentally delete the original Pictures directory? In that case simply recreating one is not enough, the system will remove configurations for it as soon as it detects that the directory doesn't exist.

Anyway, this really is simple thing to fix; just open the *~/.config/user-dirs.dirs* -file and make sure it has following line in it:

```
XDG_PICTURES_DIR="$HOME/Pictures"
```

(Doing it this way will give you back exactly the same functionality as you had by default, a pictures directory with a special icon, and recognized by the system and various programs as your pictures directory instead of just any random bookmarked location).

---

### Post by Tornikee on 2011-08-30
Thanks for the replies. I hadn't deleted the folder itself, so the 'Add bookmark' method worked just fine.
Thanks for assistance.

---

