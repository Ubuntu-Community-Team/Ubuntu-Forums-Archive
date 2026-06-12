---
title: "file list lags horribly on first listing"
date: 2011-05-03
forum: General Help
---

### Post by jfacemyer on 2011-05-03
Just upgraded to Xubuntu 11.04, and on one machine my file listing lags for quite some time (several minutes) before finally listing, then works fine for a while.

This happens in gui or on the command line.

I use autofs to mount a couple of shared nfs drives, and I'm testing to see if this is a problem (though I'm having trouble with listing any directory, not just mounted ones).

Any idea why this might be happening, or how to debug?

---

### Post by jfacemyer on 2011-05-04
Well, it appears that my other box did have the same issue. I found this page, and its fix seems to have worked on both boxes:

[http://ubuntuforums.org/archive/index.php/t-1036024.html](http://ubuntuforums.org/archive/index.php/t-1036024.html)

Doing:

```
sudo update-apt-xapian-index
```

appears to have worked!

---

