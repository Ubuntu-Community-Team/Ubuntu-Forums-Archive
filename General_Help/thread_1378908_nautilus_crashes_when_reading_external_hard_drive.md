---
title: "nautilus crashes when reading external hard drive"
date: 2010-01-12
forum: General Help
---

### Post by dogooder on 2010-01-12
Earlier tonight my computer froze when I was moving some folders on an external hard drive (ntfs) and I had to manually shut down. Now nautilus crashes whenever I try to access the drive, although if I open nautilus as root it works fine.

I'm wondering if anyone has ideas as to what went wrong or how to fix this. It's driving me crazy. Thanks.

---

### Post by dogooder on 2010-01-12
Should add this: running nautilus in terminal, when it crashes it only says "Segmentation fault".

---

### Post by dogooder on 2010-01-12
Now it's working. I think the last thing I did was  delete the ~/.local/share/gvfs-metadata folder, in case anyone else runs into this problem.

---

