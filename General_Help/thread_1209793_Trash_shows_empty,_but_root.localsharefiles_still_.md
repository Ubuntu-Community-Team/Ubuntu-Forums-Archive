---
title: "Trash shows empty, but /root/.local/share/files/ still has 18G"
date: 2009-07-10
forum: General Help
---

### Post by raymondvillain on 2009-07-10
Jaunty 32 bit.  My / partition is full.  I did some snooping around and I have a large number of music files in /root/.local/share/Trash/files and I can't get rid of them.

When I click the trash icon on the desktop, it has nothing in it.

I looked around in the posts and tried:

sudo chown -R $USER:$USER ~/.local/share/Trash

but it didn't help.

What does one do in this situation?

With gksudo nautilus, I tried to delete them graphically but that didn't work, they just popped up again with new suffixes.

---

### Post by michy99 on 2009-07-10
```
sudo rm -r /root/.local/share/Trash
```

---

### Post by raymondvillain on 2009-07-10
Thank you michy99, that did the trick.

I'm going to mark this as solved.

---

### Post by CatKiller on 2009-07-11
> **raymondvillain said:**
> I have a large number of music files in /root/.local/share/Trash/files 

...

I looked around in the posts and tried:

sudo chown -R $USER:$USER ~/.local/share/Trash

but it didn't help.

A few things.

Of course it didn't help. Those are two different directories. ~ is **your** Home directory, /root is **root's** Home directory.

Why were you deleting music files as root anyway? You should only use root permissions when you absolutely have to.

The reason the files popped back when you were using Nautilus as root is because pressing Delete moves the files to the Trash. You were looking at the location of root's Trash. Where else where they going to go? Shift-Delete deletes files rather than moving them to the Trash. Or, having opened Nautilus as root, you can select File -> Empty Deleted Items to empty root's Trash.

---

