---
title: "How to use nautilus scripts to make a &quot;send to [folder]&quot; right-click option"
date: 2009-07-26
forum: General Help
---

### Post by SEMW on 2009-07-26
I've just been trying to come up with a workaround for nautilus's somewhat hobbled "Send to" option in order to let you specify a particular folder that you often send things to (e.g. as people in [_this (archived) thread_]("http://ubuntuforums.org/showthread.php?t=82422") were trying to do).

Solution: Use nautilus scripts.

[LIST][*]Open up ~/.gnome2/nautilus-scripts
[*]Create a new empty file, and give it executable permissions (right-click, properties, 'permissions' tab)
[*]Open the file, and paste the following code in:
[/LIST]

```
#!/bin/bash
FILES=$(echo -e "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | awk 'BEGIN { FS = "\n" } { printf "\"%s\" ", $1 }' | sed -e s#\"\"##)

eval "mv -u -t /home/simon/Music/ $FILES"

exit
```
[LIST][*]Replace "/home/simon/Music/" with whatever folder you want to be able to move things to easily (remembering to escape spaces, e.g. "/my\ folder/" rather than "/my folder/")
[*]Rename the file to "Move to my folder" (or something)[/LIST]

"Move To My Folder" will now be on the right-click menu in Nautilus, under "scripts".

(Credit to [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php) for the awk & sed code that lets it handle multiple files & files with spaces).

---

