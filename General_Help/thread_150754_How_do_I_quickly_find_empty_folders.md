---
title: "How do I quickly find empty folders?"
date: 2006-03-26
forum: General Help
---

### Post by dartmusic on 2006-03-26
"Why?" you ask?  Well, I did something (probably trying the amarok replaygain script...yeah, I know, I was warned) that erased some of my music files.  It seems to be entire folders, as there are folders in my music library that are empty.  These are folders that used to hold music files...I know because I put them there myself!  I have some things on my iPod and some, well, I'm just screwed.  But, what I need to do is be able to reasonably quickly identify the empty folders within the folder that holds my music library.  There must be some fairly simple way to do this.  I've tried searching here and via google, but it's not a simple phrase to try to find.

Any ideas?

Thanks.

---

### Post by dartmusic on 2006-03-26
um...OK, I did end up finding the answer on this here very forum.

In case anyone else finds themselves in the same predicament, the answer is as follows:

find /path/you/specify -type d -empty

should be fairly self-explanatory, eh?

gave me exactly what I was looking for...and a bit of relief that I didn't actually lose that much.  whew!

thanks for taking the time to look at this.

---

### Post by ren wins on 2006-03-26
[QUOTE=dartmusic]"Why?" you ask?  Well, I did something (probably trying the amarok replaygain script...yeah, I know, I was warned) that erased some of my music files.  It seems to be entire folders, as there are folders in my music library that are empty.  These are folders that used to hold music files...I know because I put them there myself!  I have some things on my iPod and some, well, I'm just screwed.  But, what I need to do is be able to reasonably quickly identify the empty folders within the folder that holds my music library.  There must be some fairly simple way to do this.  I've tried searching here and via google, but it's not a simple phrase to try to find.

Any ideas?

Thanks.[/QUOTE]

i'm not sure it is what you're looking for, but in konqueror, you can change the viewmode to view > viewmode > filesize view.  This will give you an interesting way of glancing at a folder's contents (like ./music for instance?).  But if i remember correctly, konqueror has the annoying habit of recognizing folders as 4gb big... or maybe that's just me and my fat32 partitions.

but it's worth a shot

---

