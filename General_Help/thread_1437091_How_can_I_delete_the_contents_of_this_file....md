---
title: "How can I delete the contents of this file..."
date: 2010-03-23
forum: General Help
---

### Post by holadebob on 2010-03-23
/root/.local/share/Trash/files/

I have a tar backup file in there and can't get rid of it. I've tried from root with Nautilus, the files disappear for a couple of seconds and then reappear.
thank you,
Bob

---

### Post by patchwork on 2010-03-23
Have you tried sending it to the 'blackhole'?

EDIT:removed...dangerous command

---

### Post by linden940 on 2010-03-23
very nice backups...you delete them and they just COME right back!!!...wish my backup files worked like that when i "clicked wrong butten"

well have you tryed to delete the file IN sudo?

---

### Post by -grubby on 2010-03-23
In that case, I think there's a problem with Nautilus.

Try this in the terminal (replacing appropriately of course):

```

sudo rm /root/.local/share/Trash/files/whatever_your_backup_is_named

```

EDIT: Oh, I guess there wasn't a problem with Nautilus. patchwork was actually browsing Nautilus' trash directory, and then deleted something from it, which translated to "send to trash" to Nautilus so it tried to move it to the same place it already was, and nothing happened.

---

### Post by diesch on 2010-03-23
> **patchwork said:**
> Have you tried sending it to the 'blackhole'?

```
 sudo mv /path/filename /dev/null
```

**Don't do this!**

It **replaces** the device file */dev/null* with the ordinary file */path/filename*. So after that */dev/null* is just a plain normal file that stores any data you write to it.

---

### Post by diesch on 2010-03-23
> **holadebob said:**
> /root/.local/share/Trash/files/

I have a tar backup file in there and can't get rid of it. I've tried from root with Nautilus, the files disappear for a couple of seconds and then reappear.


The standard delete in Nautlius is actually a "move to trash". Moving a file from trash to trash doesn't change much ;-)

Either activate the real delete command at the nautilus settings or use the command line es suggested by -grubby

---

### Post by patchwork on 2010-03-23
Aye........my mistake....bad joojoo.

Hope you didn't try this...

My apologies.

---

### Post by holadebob on 2010-03-23
Hi, just got back from work and thanks for coming back on the error. Diesch, you divulged my embarrassment. I hope someone else does sends their trash to trash so I ain't the only goof.
How stupid of me.
I switched the options to get the delete function and it works fine, of course.
When I am a noobie (excuse?) or confused at all the Trashes, I fell into it.
Thank you.
Humble over and out.

---

