---
title: "Clearing Totem history 2010"
date: 2010-08-30
forum: General Help
---

### Post by ex_isp on 2010-08-30
Totem seems to have no way to clear history.  In older Ubuntu Versions, there was an option in "places" to clear "recent history".  Seems, no longer is it there.

My solution is to go into your home directory, 
type:  
ls -la

This will display all files.  Find file ".recently-used.xbel " and
type:
rm .recently-used.xbel 

This will remove all totem and much other history.  (Admins, please interject if this takes out too much... it was my solution and resolved ALOT of clutter.)

Next type:
touch .recently-used.xbel 

This will recreate said recent history file, but it will now be empty.
This will also add non- default read permissions -rw-r--r-- (default this
file should be -rw-------- if I recall).

Thought I would post this as I found no other history clearing option for totem in searches newer than Sept09, in which those options, no longer are available.

Again, Gurus, please comment if you spot something "off" in this post.

Thanks,

Ex

---

### Post by wojox on 2010-08-30
I've always done it this way

```
gedit .gtkrc-2.0
```

Add

```
gtk-recent-files-max-age=0
```

Next reboot your all set.

---

### Post by ex_isp on 2010-08-30
Nice!  thanks, is better solution than mine.  And, I discovered already mine is flawed.  After running my solution, totem shows no history until I open ONE thing.  Then all history is back.  Had to manually edit .recent.......  file.   That worked, but your IS better.

Gotta love this forum!

Thanks again

Ex

---

