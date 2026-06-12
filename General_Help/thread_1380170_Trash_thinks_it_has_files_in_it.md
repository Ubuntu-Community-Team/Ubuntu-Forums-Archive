---
title: "Trash thinks it has files in it"
date: 2010-01-13
forum: General Help
---

### Post by Tribulation on 2010-01-13
I put a couple of files into the trash yesterday and decided that I'd rather keep them so I put them back where they came from. For some reason though, the trash insists that it still has two items in it. I've tried to empty it and I've restarted but still it says that it contains two items. Any idea why this would be or how to fix it?

---

### Post by xifer on 2010-01-13
Not had this problem.  

Is this gnome/kde/other?

How the files were deleted?

How they were  restored?

what's in $HOME/.local/share/Trash

```

cd
ls -lR .local/share/Trash

```


you could probably delete that dir and it would be recreated next time it was used.

---

