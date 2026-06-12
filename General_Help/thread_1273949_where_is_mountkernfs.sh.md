---
title: "where is mountkernfs.sh?"
date: 2009-09-24
forum: General Help
---

### Post by clarknova on 2009-09-24
I really like implementing the changes to mountkernfs.sh, as outlined here:
[http://www.staldal.nu/tech/2008/07/26/linux-with-mounted-read-only/](http://www.staldal.nu/tech/2008/07/26/linux-with-mounted-read-only/)

Life happens faster in RAM, and hey, why write to the SSD any more than necessary?

So I just installed the Karmic alpha-6 on my laptop and was disappointed to find mountkernfs.sh nowhere in the filesystem.

But obviously something is mounting /proc and /sys and so forth, so where would be the new best place to add my own mounts?

---

### Post by trinaryouroboros on 2010-01-27
I'm shocked noone has responded to this thread, I originally was going to hunt this down in regards to VirtualBox on Karmic, but I found out later I didn't need it after all.

---

### Post by clarknova on 2010-01-27
This is the reason I was looking:
[http://www.staldal.nu/tech/2008/07/26/linux-with-mounted-read-only/](http://www.staldal.nu/tech/2008/07/26/linux-with-mounted-read-only/)

But thanks to an update to this blog, it's no longer an issue for me:
[http://www.staldal.nu/tech/2009/11/15/linux-with-mounted-read-only-2-0/](http://www.staldal.nu/tech/2009/11/15/linux-with-mounted-read-only-2-0/)

---

