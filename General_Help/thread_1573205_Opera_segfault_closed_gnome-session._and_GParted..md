---
title: "Opera segfault closed gnome-session. and GParted."
date: 2010-09-12
forum: General Help
---

### Post by JustinR on 2010-09-12
Hey everybody - I have a little problem here.

I was using GParted to move and resize a few partitions on my external HDD that I use for backup purposes. Well while this was going on, I was using Opera to reply to a post on the forums and Opera segfaulted, which in turn crashed GNOME. Gnome restarted, I logged back in, my external HDD was still reading/writing furiously and GParted won't open.

So I know that the GParted I started is still running, although the handle that GParted had on its GUI is still locked - so I can't open a new GParted GUI - and the existing GParted GUI has closed - so now I can't check on the progress of my partition operation.

I'm assuming everything will complete okay in a few hours? Has anybody had any experience with this? Can I check on the progress somehow?

Thanks. :)

---

### Post by TeoBigusGeekus on 2010-09-12
Oh oh!!
Leave your pc on for as long as you can...
I've lost 500GB of data by a gparted crash once, but it's taught me never to do anything else while gparted's on.
Good luck...

---

### Post by JustinR on 2010-09-18
> **TeoBigusGeekus said:**
> Oh oh!!
Leave your pc on for as long as you can...
I've lost 500GB of data by a gparted crash once, but it's taught me never to do anything else while gparted's on.
Good luck...

I waited for around 7 hours, and looked at DMESG and gparted craashed. Darn............................... I lost most of the data - but its nothing I can't fix.

---

