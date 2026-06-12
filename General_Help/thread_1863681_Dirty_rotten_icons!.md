---
title: "Dirty rotten icons!"
date: 2011-10-18
forum: General Help
---

### Post by Shibblet on 2011-10-18
Alright, here is a screenshot of one of my video file folders.  Notice the one icon is just a "filmstrip" icon, and the rest are actual screenshots from the video file itself.  

How do I get Ubuntu to "re-scan" the file to update the icon to a screenshot like the rest of the files in the directory?  I've pressed F5 to refresh the window, but it doesn't do anything.

---

### Post by Grenage on 2011-10-18
I've had this many times before, and rarely did I 'fix' it.  Moving the files into a new folder often worked, as did clearing the thumbnail cache; the cache is stored in:

```
~/.thumbnails/
```

---

### Post by matt_symes on 2011-10-18
Hi

You could delete the thumbnails in the thumbnail folder in your home directory.
```

find ~/.thumbnails -type f -exec rm {} \;
```

Something like that should do it.

Kind regards

---

### Post by mc4man on 2011-10-18
It's possible that just clearing the fail/gnome-thumbnail-factory folder will take care of, in - 
~/.thumbnails/fail/gnome-thumbnail-factory

---

