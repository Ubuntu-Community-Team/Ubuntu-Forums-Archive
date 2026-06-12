---
title: "rtorrent.rc location"
date: 2010-10-24
forum: General Help
---

### Post by baddnady23 on 2010-10-24
Hello all, I am in the process of setting up a torrent slave.  After I have configured my rtorrent.rc configuration file to what I want, where is the appropriate location to save it to so that rtorrent will use those settings?  I keep seeing something about it being in ```
./.rtorrent.rc
``` but it didn't seem as if it was working there for me...  I copied it over to ```
/etc/init.d
``` and now it seems to be working...is that wrong or is it just me?

---

### Post by TeoBigusGeekus on 2010-10-25
```
~/.rtorrent.rc
```
It needs to be placed in your home folder.
It's amazing (though logical) that it works putting it in /etc/init.d

---

