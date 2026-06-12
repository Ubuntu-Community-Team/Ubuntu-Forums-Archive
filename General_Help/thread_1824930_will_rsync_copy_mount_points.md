---
title: "will rsync copy mount points?"
date: 2011-08-14
forum: General Help
---

### Post by baddnady23 on 2011-08-14
If I have rsync set up to back up my /home directory,  and I have a separate hard drive mounted in /home/me/music to store all my music on, will rsync copy the contents of that separate drive that I have mounted in the music folder to or will it skip over those files?

---

### Post by papibe on 2011-08-18
By default, yes. But you can avoid it if you want, e.g.:
```
$ rsync -av --one-file-system   origin/ destination/
```
Regards.

---

### Post by seawolf167 on 2011-08-18
You can also exclude a directory or directories from rsync, the man page is pretty helpful

```
man rsync
```

---

