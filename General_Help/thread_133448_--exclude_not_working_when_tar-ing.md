---
title: "--exclude not working when tar-ing"
date: 2006-02-20
forum: General Help
---

### Post by harty83 on 2006-02-20
I'm trying to backup my system the manual way to my external harddrive by:
```
tar cvpjf /media/sda1/backup.bz2 / --exclude=/media
```

However, it is still trying to backup the media folder along with sda1 (I kill it before it gets too far)!  That's bad because it will recursively backup my external as well.  What am I doing wrong?

Thanks!

---

