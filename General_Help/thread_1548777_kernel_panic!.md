---
title: "kernel panic!"
date: 2010-08-08
forum: General Help
---

### Post by Forithan on 2010-08-08
hey there, just got a quick question. im running linux mint on my desktop, and for some reason today, when i went to boot up my computer, i received this message: 

3.592202 kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

i really do not want to lose the information on these drives, and i have attempted accessing them via an external drive, but to no avail. does anybody have any clue as to why this happened? :-( 

any help is greatly appreciated!

thanks

---

### Post by sandyd on 2010-08-08
> **Forithan said:**
> hey there, just got a quick question. im running linux mint on my desktop, and for some reason today, when i went to boot up my computer, i received this message: 

3.592202 kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

i really do not want to lose the information on these drives, and i have attempted accessing them via an external drive, but to no avail. does anybody have any clue as to why this happened? :-( 

any help is greatly appreciated!

thanks
a) don't panic
b) stop trying to access your files. If their lost, the less you touch them the more you will recover using file recovery programs. The more you touch them, the less chance we can recover them.
c) boot up to a livecd and run
```

sudo fdisk -l
```

---

