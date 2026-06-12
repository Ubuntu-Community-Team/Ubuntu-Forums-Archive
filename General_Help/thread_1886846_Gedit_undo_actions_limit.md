---
title: "Gedit undo_actions_limit"
date: 2011-11-25
forum: General Help
---

### Post by tzjin anthony ks on 2011-11-25
Howdy.

I just realized that the new version of gedit limits the number of actions that can be undone. I used to be able to set it to unlimited, by simply changing the undo_actions_limit parameter to -1 in the .gconf/ directory, but with the new unity desktop, it seems to have been moved elsewhere.

Could someone tell me how to set the number to unlimited?

Thanks.

Tzjin.

---

### Post by Vaphell on 2011-11-25
11.10?
```
sudo apt-get install dconf-tools
dconf-editor
```

org.gnome.gedit.preferences.editor.max-undo-actions

---

### Post by tzjin anthony ks on 2011-11-25
Thanks, mate ! Cheers.

---

### Post by tzjin anthony ks on 2011-12-11
That seemed to work -- However, there seems to be something stranger going on:

Particularly, if I leave my editor open for a few hours, with edits made to multiple files, I don't seem to be able to undo all the edits I've done.

It seems really weird, but was just wondering if anyone might have some thoughts.

Thanks.

---

