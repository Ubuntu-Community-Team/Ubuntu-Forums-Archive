---
title: "Show files that appear as &quot;Only in&quot; using diff"
date: 2010-01-10
forum: General Help
---

### Post by altonbr on 2010-01-10
Using ```
diff -ur dir1/ dir2/ > diff.diff
```I want all files that say "Only in path/ file/folder" to actually display the content of these files/folders.

You can rid any comparisons of files by adding the '-q' flag so that all it says is "Only in ...", but I want to do the opposite.

I'm trying to copy .gconf of a vanilla Ubuntu, modify the gnome-panel settings and then compare what has changed so I can write the changes in a script and use gconftool-2 to make it automated for other installations.

I would go through every folder and file manually, but there must be at least 30 file and folder changes after I'm done adjusting the settings of gnome-panel.

Thanks!

---

