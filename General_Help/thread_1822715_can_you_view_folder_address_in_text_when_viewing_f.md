---
title: "can you view folder address in text when viewing folders in a window"
date: 2011-08-10
forum: General Help
---

### Post by fuzzylogic25 on 2011-08-10
Currently, whenever we open a folder like "media/DATA/Work/Projects/Linux" at the top of the window it views each folder/subfolder as a button like [media] [DATA] [Work] [Projects] [Linux]. So if you click a folder named "Ubuntu" within the "Linux" folder another button [Ubuntu] will be added.

I like this feature, but often i find myself needing to copy and paste that address somewhere and all I can do really is type it out manually. Is there a way to also display the address location in text like "media/DATA/Work/Projects/Linux"??

---

### Post by papibe on 2011-08-10
Control+L should let you convert the graphic path to a string that you can copy, and then paste anywhere.

Hope it helps.

---

### Post by darkhelmetchris on 2011-08-10
You sure can.

Open your Configuration Editor (gconf-editor) and activate the key "always_use_location_entry"

```
user@host~$ gconf-editor
```
Then find the path:
/apps/nautilus/preferences/always_use_location_entry
and activate that check.

You're all set.

---

