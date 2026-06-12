---
title: "preview icon for MPEG files"
date: 2011-01-30
forum: General Help
---

### Post by Keith_Beef on 2011-01-30
Ubuntu 9.10 and Gnome 2.28.1

I have a set of MPEG-4 files, all created by Handbrake, sitting in a directory.

Most of them have an icon that shows a still from the video content, but four of them have the generic "film spool" icon.

So, two questions... 

[LIST=1]
[*]Why do some of these files have that generic "film spool" icon?
[*]How can I choose the frame to be used as the icon?
[/LIST]

K.

---

### Post by asmoore82 on 2011-01-30
Delete all the files from "$HOME/.thumbnails/fail/gnome-thumbnail-factory/"

This will force nautilus to retry generating thumbnails for files that previously failed.
Thumbnailing could have failed on those few files because you happened to have
the folder open in nautilus when handbrake first started writing the files.

---

### Post by Keith_Beef on 2011-01-30
> **asmoore82 said:**
> Delete all the files from "$HOME/.thumbnails/fail/gnome-thumbnail-factory/"

This will force nautilus to retry generating thumbnails for files that previously failed.
Thumbnailing could have failed on those few files because you happened to have
the folder open in nautilus when handbrake first started writing the files.

Thanks, that solved the problem of the generic film-spool icon. Now all files have a still from the video content.

Is there any way for me to choose which frame this comes from?

---

