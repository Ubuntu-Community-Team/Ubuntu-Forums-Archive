---
title: "No space on hard drive after using Photorec"
date: 2012-10-10
forum: General Help
---

### Post by meijin3 on 2012-10-10
As the title suggests, I recently used Photorec on my computer and scanned my hard drive using the "whole" setting. After deleting the folder that I sent the files to, I still have no space left over. Anyone want to help with a solution? :)

[IMG]http://i.imgur.com/mOfx2.png[/IMG]

---

### Post by SlugSlug on 2012-10-10
press Ctrl+h  to show hidden files

---

### Post by meijin3 on 2012-10-10
In my trash bin? Nothing shows up there.

---

### Post by SlugSlug on 2012-10-10
There will be a .Trash folder (there may also be other hidden files)

In a terminal you can also 

sudo du -ch /path/to/media

---

### Post by meijin3 on 2012-10-10
I was able to find the /home/emilio/.local/share/Trash/expunged directory. When I delete those files, they go to /home/emilio/.local/share/Trash/files. When I empty the recycle bin, they go back to /home/emilio/.local/share/Trash/expunged

---

### Post by SlugSlug on 2012-10-10
> **meijin3 said:**
> I was able to find the /home/emilio/.local/share/Trash/expunged directory. When I delete those files, they go to /home/emilio/.local/share/Trash/files. When I empty the recycle bin, they go back to /home/emilio/.local/share/Trash/expunged


```
sudo rm -Rf /home/emilio/.local/share/Trash/
```

---

### Post by meijin3 on 2012-10-10
> **SlugSlug said:**
> ```
sudo rm -Rf /home/emilio/.local/share/Trash/
```

Seems to have worked. Thanks so much!

---

### Post by SlugSlug on 2012-10-10
no prob :)

---

