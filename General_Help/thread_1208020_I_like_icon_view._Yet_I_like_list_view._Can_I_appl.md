---
title: "I like icon view. Yet I like list view. Can I apply these recursively?"
date: 2009-07-08
forum: General Help
---

### Post by Roasted on 2009-07-08
Music - I love viewing music as list view. I can fit more on the screen and navigate much quicker.

Pictures - However with picture I love icon view so I can see the thumbnails of each picture to get an idea of what each picture is. Since I take so many pictures, I leave them with their default name and don't care to spend several days of my life trying to come up with legit names of each picture on my system.

But - how can I apply these recursively? It would be SO convenient for ALL folders, sub folders, files, etc within "Music" to appear in list view, while everything in "Pictures" appears in icon view.

Is this possible?

---

### Post by CatKiller on 2009-07-08
Nautilus does remember the view that you select for a folder. I believe that it does this by storing an XML file in ~/.nautilus/metafiles that references the name of the folder and contains the view that you've selected. There may be some other mechanism too. I don't know enough about either XML or Nautilus to know whether you could use some kind of recursive or wildcard option in this file. Otherwise, it might be possible to write a script that runs recursively through the directories that you're interested in and generates appropriate XML files in that directory.

---

