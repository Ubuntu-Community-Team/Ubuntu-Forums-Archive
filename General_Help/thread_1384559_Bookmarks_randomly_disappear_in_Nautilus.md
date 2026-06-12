---
title: "Bookmarks randomly disappear in Nautilus?"
date: 2010-01-18
forum: General Help
---

### Post by DemonSharkKisame on 2010-01-18
Does anyone else have this issue? Sometimes, one of my bookmarks (Documents, Music, Pictures, and Videos) will randomly disappear from the list in Nautilus, and it seems to also affect the Places menu and Thunar as well. The directories are obviously still there, but the bookmarks randomly disappear! Any way to fix this?

---

### Post by tom.swartz07 on 2010-01-27
> **DemonSharkKisame said:**
> Does anyone else have this issue? Sometimes, one of my bookmarks (Documents, Music, Pictures, and Videos) will randomly disappear from the list in Nautilus, and it seems to also affect the Places menu and Thunar as well. The directories are obviously still there, but the bookmarks randomly disappear! Any way to fix this?

Same thing happened to me the other day- Cant figure it out- Ill post if I find something in the meantime.

Anyone else know?

---

### Post by tom.swartz07 on 2010-01-29
Ive figured it out. 

In my case, it turned out that the file that holds the bookmarks .gtk-bookmarks was corrupt


Look and see if you still have a file like that and if so, delete it. Navigate to your home directory and type ```
sudo ls -lia
```

Post that back here for reference.

it will list every file in your home folder, including 'really' hidden ones.

Just delete .gtk-bookmarks and then you should be all set!




If you run into a problem removing it, post back and let us know! 
Also, let me know if it worked- Im just curious if you had the same problem

---

### Post by DemonSharkKisame on 2010-01-30
Hmm... I went into my gtk-bookmarks file, and all I had to do was correct my Videos bookmark (there were two "Videos" instead of the usual one).

---

### Post by beagle1 on 2012-07-09
I am running letest Ubuntu 12.04.
All of a sudden, my firefox bookmarks dissappeared.  I also notice a few font and highlighting differences in the browser.

I removed the .gtk-bookmark file; the problem still persists.

In the past 2 months, I am experiencing the problem for the second time.  First time the problem appeared, I did a complete reinstall of Ubuntu.

Any help is appreciated.

B1

---

### Post by wildmanne39 on 2012-07-09
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

