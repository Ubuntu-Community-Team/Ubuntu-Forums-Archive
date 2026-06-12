---
title: "Mount subdirectory --&gt; work-around or bug"
date: 2010-09-20
forum: General Help
---

### Post by UncleBoarder on 2010-09-20
I want to mount my "Ubuntu" subdirectory (second drive) and have it show up as a "data" volume on my desktop.

This works, can someone explain if this is a bug?  Or a valid workaround?

mount /dev/sdb1 /media/data
mount --bind /media/data/Ubuntu /media/data

I'm overwriting the mounted volume with a subdirectory.  It's important to note, once a volume is mounted to media, a second mount of the same volume (even though successful) will not display a new icon. - (no one seemed aware of this "feature" of Ubuntu in one of my previous posts)

If someone has a concern with the fact that I'm using the same mount point I'm remounting, I'll use a different initial volume.

Bottom line, I want to mount a subdirectory and have it show on the desktop.  To date this is the only method I've found that works.

---

