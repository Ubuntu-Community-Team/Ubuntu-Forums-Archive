---
title: "Can't delete files, claims trash is full."
date: 2009-08-16
forum: General Help
---

### Post by MdaG on 2009-08-16
Hi, I can't seem to delete files using Dolphin. It only claims the trashcan is full, but as far as I can see it should be empty.

```
$ du .local/share/Trash/
144     .local/share/Trash/info
116     .local/share/Trash/files
264     .local/share/Trash/
```

---

### Post by lessgov2007 on 2009-08-16
I really don't know what would be causing that issue. Just as a guess, have you checked to make sure the root trash folder isn't full? /root/.local/share... If so, you can just shift+del the Trash folder. Like I said, I dunno if this is your problem I'm only guessing. Hope someone can help you if not.

---

### Post by MdaG on 2009-08-17
Thanks for your reply.
Checking the root folder I see that it's almost empty so that can't be it. :(
```
$ sudo du /root
8       /root/.dbus/session-bus
12      /root/.dbus
12      /root/.config
8       /root/.kde/share/config/kresources/contact
8       /root/.kde/share/config/kresources/calendar
8       /root/.kde/share/config/kresources/notes
28      /root/.kde/share/config/kresources
168     /root/.kde/share/config
40      /root/.kde/share/apps/kconf_update/log
44      /root/.kde/share/apps/kconf_update
48      /root/.kde/share/apps
220     /root/.kde/share
224     /root/.kde
260     /root
```

---

### Post by credobyte on 2009-08-17
Try:
```
sudo rm -r $HOME/.local/share/Trash/files/*

```

Also, can you post the output of the following command?
```
df | grep /dev/sda1
```

---

### Post by MdaG on 2009-08-17
OK, here's the output:
```
$ sudo rm -r $HOME/.local/share/Trash/files/*
rm: cannot remove `/home/magnus/.local/share/Trash/files/*': No such file or directory
```
I'll assume this means there's nothing to remove.

```
$ df | grep /dev/sda1
/dev/sda1              9614116   3333956   5791788  37% /
```
There seems to be plenty of space left.

*Edit*
The problem was resolved by force deleting some files using shift + del. After that the Trashcan went back to normal.  **?????**
Anyway, thanks for the help. :)

---

