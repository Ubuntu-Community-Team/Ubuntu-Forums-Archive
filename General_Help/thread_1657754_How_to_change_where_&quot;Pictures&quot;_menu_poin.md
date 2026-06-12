---
title: "How to change where &quot;Pictures&quot; menu points to"
date: 2011-01-01
forum: General Help
---

### Post by kd4hey on 2011-01-01
I had found this before, but can't seem to stumble across it now.

I keep a separate partition for my data (Pictures, Music, Documents, etc) & want the "Pictures" item in the Places Menu to point to the correct place.

How do I access this?

Thanks in advance for the help.

---

### Post by Seq on 2011-01-01
The configuration is stored in the file "~/.config/user-dirs.dirs". You can edit it manually with a text editor.

---

### Post by rickcjmac on 2011-01-01
This might help:

[http://ubuntuforums.org/showthread.php?t=955432](http://ubuntuforums.org/showthread.php?t=955432)

Good luck :)

---

### Post by kd4hey on 2011-01-01
Thanks guys,

I thought that got it, but I modify the file, save it, close it & re-open to verify the changes, but the "Pictures" link does not change.  Upon re-boot, the file gets re-written back to the original.

Am I missing something?

---

### Post by kherring7383 on 2011-01-01
Although there are several ways to change this, I find using Ubuntu Tweak the easiest.
Once you've installed Ubuntu Tweak, Under the Personal Section, you can change any of the default folder settings.

---

### Post by gerowen on 2011-01-01
> **kd4hey said:**
> Thanks guys,

I thought that got it, but I modify the file, save it, close it & re-open to verify the changes, but the "Pictures" link does not change.  Upon re-boot, the file gets re-written back to the original.

Am I missing something?

```
sudo killall nautilus gnome-panel
```

Should restart the affected apps after modifying the file.  The way I'd do it is just open a folder, any folder.  Click "Bookmarks", then "Edit Bookmarks".  The Pictures link is in there.

---

### Post by sgosnell on 2011-01-01
Bookmarks/Edit Bookmarks in Nautilus is the way to go.

---

### Post by kd4hey on 2011-01-01
> **gerowen said:**
>   The way I'd do it is just open a folder, any folder.  Click "Bookmarks", then "Edit Bookmarks".  The Pictures link is in there.


OUTSTANDING!!!  That's what I had stumbled into before.  Thanks!

By simply deleting the existing bookmarks, then navigating to the folders I wanted to be on the "Totem Pole" & clicking "Add Bookmark" for each one, I was able to re-create the list with my new folders in place.

Thanks so much!

SOLVED!

---

