---
title: "Remove Directory Terminal Command Help"
date: 2011-07-11
forum: General Help
---

### Post by strange_cathect on 2011-07-11
Hi, I have a directory in my / folder called "Backup."

I'm trying to delete it, but have not been successful. I'm using the command:sudo rmdir /Backup

When I execute, I get an error: 

> rmdir: failed to remove `/Backup': Device or resource busy


How can I get rid of this? Thanks!

---

### Post by CharlesA on 2011-07-11
Run this to see what is using that folder:

```
sudo lsof /Backup
```

---

### Post by strange_cathect on 2011-07-11
I get:
> 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/alan/.gvfs


---

### Post by CharlesA on 2011-07-11
> **strange_cathect said:**
> I get:
That's a normal error if you run that as root.

Was there anything else listed?

---

### Post by strange_cathect on 2011-07-11
That was all of it.

---

### Post by CharlesA on 2011-07-11
Have you rebooted already?

---

### Post by Surendil on 2011-07-11
did you try:
```
sudo rm -f -r /Backup 
```

---

### Post by strange_cathect on 2011-07-11
Nope. I'll try it. 

Thanks for your help on this!

---

### Post by strange_cathect on 2011-07-11
No dice. It is still there.

Hm. I tried to rm it again and it worked. 

Thanks for the help on this...thought I was losing my mind.

---

