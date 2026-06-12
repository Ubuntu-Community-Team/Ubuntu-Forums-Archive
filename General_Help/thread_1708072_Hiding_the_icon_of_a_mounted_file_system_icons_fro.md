---
title: "Hiding the icon of a mounted file system icons from desktop"
date: 2011-03-16
forum: General Help
---

### Post by nkae100 on 2011-03-16
10.04 LTS:

Is there a way to hide an icon of a mounted file system from the GNOME desktop?

---

### Post by nothingspecial on 2011-03-16
Alt-F2

```
gconf-editor
```

apps > nautilus > desktop

uncheck/tick volumes visible.

Not sure how you do it for specific ones though or if you can.

---

### Post by nkae100 on 2011-03-16
Thanks dude, you've been a help.


Also, funny quote you've got there.. So, annoyingly true. :P

---

### Post by mcduck on 2011-03-16
> **nothingspecial said:**
> Alt-F2

```
gconf-editor
```

apps > nautilus > desktop

uncheck/tick volumes visible.

Not sure how you do it for specific ones though or if you can.

For a specific drive the method is as simple as configuring that drive to mount anywhere else than inside /media or your home directory.

/mnt would be a good location, for example.

---

### Post by nkae100 on 2011-03-16
Ahhh, thanks for the info mate!

Someone else suggested /mnt to me, however the directory did not exist.

---

### Post by mcduck on 2011-03-16
> **nkae100 said:**
> Ahhh, thanks for the info mate!

Someone else suggested /mnt to me, however the directory did not exist.

check again, it _definitely_ exists on any normal Linux install... :D

---

### Post by nkae100 on 2011-03-16
haha yeah, I just realized... On my very first week of using Ubuntu (my first propper use of using Linux also) I deleted all the empty directories in /. lol ignorant noob. Thanks, I will re-create the directory later on tonight and mount at that point. :)

---

### Post by Krytarik on 2011-03-16
> **mcduck said:**
> For a specific drive the method is as simple as configuring that drive to mount anywhere else than inside /media or your home directory.

/mnt would be a good location, for example.
Doing it that way would also remove it from the "Places" menu, unless you create a "Bookmark" for it instead.

---

### Post by mcduck on 2011-03-16
> **Krytarik said:**
> Doing it that way would also remove it from the "Places" menu, unless you create a "Bookmark" for it instead.

Yes, that's right. You can't have a (single) mounted drive appearing automatically in the Places menu but not on the desktop.

So you need to either create a bookmark for it, or do what I do and symlink the drive into your home directory. :)

---

