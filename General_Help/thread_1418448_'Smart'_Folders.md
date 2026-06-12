---
title: "'Smart' Folders"
date: 2010-02-28
forum: General Help
---

### Post by steev182 on 2010-02-28
I'm looking for something in Ubuntu (o Linux) that would put newly added and unwatched video files into a folder.

Are there any ways of doing this?

---

### Post by Barriehie on 2010-03-01
> **steev182 said:**
> I'm looking for something in Ubuntu (o Linux) that would put newly added and unwatched video files into a folder.

Are there any ways of doing this?

Probably more than one way to do this but what I do for newly dl'ed images is have a script running and it uses **inotifywait** to watch the folder and when a file is created it renames it and moves it to another directory.  I doubt it can tell if the file has been watched but it can definitely determine if it's been newly added.  Might have to install **inotify-tools** to use it.

---

