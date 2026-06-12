---
title: "Symbolic Links"
date: 2010-01-18
forum: General Help
---

### Post by damitch on 2010-01-18
```
david@goodwill-desktop:/media/KINGSTON/JavaProjects/bin$ ln -s ./Settings.xml ./SettingsLink
ln: creating symbolic link `./SettingsLink': Operation not permitted
david@goodwill-desktop:/media/KINGSTON/JavaProjects/bin$ 
```

*[Various other attempts omitted - all with similar results]*

Why might this be?

As ever, many thanks for help.

---

### Post by Leppie on 2010-01-18
> **damitch said:**
> ```
david@goodwill-desktop:/media/KINGSTON/JavaProjects/bin$ ln -s ./Settings.xml ./SettingsLink
ln: creating symbolic link `./SettingsLink': Operation not permitted
david@goodwill-desktop:/media/KINGSTON/JavaProjects/bin$ 
```*[Various other attempts omitted - all with similar results]*

Why might this be?

As ever, many thanks for help.
did you put yourself in the fuse group, or do you have to enter your password to mount the usb stick?
to add yourself to the fuse group:
```
sudo adduser david fuse
```

---

### Post by michy99 on 2010-01-18
What are the permissions for that directory?```
ls -ld /media/KINGSTON/JavaProjects/bin
```

---

