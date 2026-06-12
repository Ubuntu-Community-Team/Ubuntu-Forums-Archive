---
title: "HD available space decreasing automatically"
date: 2009-12-21
forum: General Help
---

### Post by tumateix on 2009-12-21
Hey, something a little bit paranormal it's happening to me: my HD's available space is decreasing automatically. 

I don't install anything and I don't download anything (in fact I've freed up a lot of space by deleting files), but when I restart my computer the available space slowly decreases from 7-8 GB to 0 (in 30-40 minutes or so).

I am running Karmic in single 135 GB partition, so no Windows indexation interferences.

I think it may be some useless process uselessly taking up more and more memory, but I don't know how to solve it. 


Any idea is wellcome!

Thanks!

---

### Post by tumateix on 2009-12-21
I've got some news.

I've run Baobab (the disk usage analyzer) and I've found that everything is normal, except that there's a folder that it's up to 40GB!

```
/usr/share/images
```

I think this is not normal, but I'm not sure what to do about it. 

Inside this folder I've found a another folder named xplash that contains lots of image backups (files named "backup.[insert here a long number that apparently means the date]") of the same /usr/share/images folder, so... is it backing up itself? Is this normal? How can I stop it if it's not?

Thank you!

EDIT: every backup file includes all the previous backup files so its size increases exponentially LOL it's very stupid!

---

### Post by tumateix on 2009-12-21
New update!

I've finally found that the problem was an script I downloaded from gnome-look.org that sets the xplash background as the desktop background. This script was automatically run at every startup, that's when the useless backups took place.

I've removed the script and the HD space no longer decreases pointlessly. But now I'd like to know what can be removed in the folder I posted previously, in order to not to destroy anything... any idea?

---

### Post by tumateix on 2009-12-21
If someone's interested, I finally deleted everything :D

---

### Post by lotharmat on 2009-12-21
> **tumateix said:**
> If someone's interested, I finally deleted everything :D

I'm interested!:)

---

