---
title: "Can I globally set all file types to the list option?"
date: 2010-05-13
forum: General Help
---

### Post by HandLotion on 2010-05-13
I upgraded to Lucid this week (great), but somehow managed to set all the file options to default of icons view.  Can I globally change this to set everything to show in a list view?  For that matter, can I globally set the view to always show all the hidden files? I'm going crazy doing this on a directory by directory basis.

---

### Post by ABCC on 2010-05-13
> **HandLotion said:**
> I upgraded to Lucid this week (great), but somehow managed to set all the file options to default of icons view.  Can I globally change this to set everything to show in a list view?  For that matter, can I globally set the view to always show all the hidden files? I'm going crazy doing this on a directory by directory basis.

Open up gconf-editor and navigate to the key /apps/nautilus/preferences/default_folder_viewer and change it from "icon_view" to "list_view". For hidden files toggle /desktop/gnome/file_views/show_hidden_files.

hth,

ABCC

---

### Post by amite on 2010-05-13
you can use following command :
chmod -Rv xxx ~/

---

### Post by amite on 2010-05-13
If you have any other doubts regarding use of chmod use 
$ man chmod

---

### Post by HandLotion on 2010-05-13
Thanks ABCC. My first use of the gconf-editor - exactly what I was looking for.

---

### Post by ABCC on 2010-05-13
> **HandLotion said:**
> Thanks ABCC. My first use of the gconf-editor - exactly what I was looking for.

Incidentally, the list/icon/etc setting is also configurable in the edit>preferences dialog in nautilus, as is the hidden files setting.

I don't see why chmod would be appropriate here.....

ABCC

---

### Post by sallymc on 2010-07-22
> **ABCC said:**
> Incidentally, the list/icon/etc setting is also configurable in the edit>preferences dialog in nautilus, as is the hidden files setting.

I don't see why chmod would be appropriate here.....

ABCC

You are SO clever ABCC.  Such a simple answer, and it works like a charm.  Preferences is such a useful tool, and I always overlook it, thus forgetting its magic.  Many thanks indeed

---

