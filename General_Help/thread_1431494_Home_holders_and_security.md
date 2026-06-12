---
title: "Home holders and security"
date: 2010-03-16
forum: General Help
---

### Post by Muscovy on 2010-03-16
I recently noticed that user's home folders have read capabilities for other users. I want to add a chmodding of something like 700 to home folders, which I assume won't break anything, and secondly, how should I set it up on a LiveCD? The only way I know I could do is make a script in /etc/skel/.config/autostart that chmods the folder, then deletes itself. Anyone have any more elegant ideas?

---

### Post by dcstar on 2010-03-17
> **Muscovy said:**
> I recently noticed that user's home folders have read capabilities for other users. I want to add a chmodding of something like 700 to home folders, which I assume won't break anything, and secondly, how should I set it up on a LiveCD? The only way I know I could do is make a script in /etc/skel/.config/autostart that chmods the folder, then deletes itself. Anyone have any more elegant ideas?

Change the default DIR_MODE:
```
gksudo /etc/adduser.conf
```

---

