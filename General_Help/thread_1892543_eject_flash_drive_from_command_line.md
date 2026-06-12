---
title: "eject flash drive from command line?"
date: 2011-12-08
forum: General Help
---

### Post by cortman on 2011-12-08
And a real simple question. How can I unmount and safely eject a flash drive from the command line?

---

### Post by Lars Noodén on 2011-12-08
You would use [umount](http://manpages.ubuntu.com/manpages/precise/en/man8/umount.8.html), but you have to know where it is mounted first.

```

sudo umount /media/*somedisk*

```

You can use [mount](http://manpages.ubuntu.com/manpages/precise/en/man8/mount.8.html) or [df](http://manpages.ubuntu.com/manpages/precise/en/man1/df.1posix.html) to see what you have mounted.  Pick your flash drive from the list.

(Note that the spelling is *u*mount and not *un*mount.)

---

### Post by WorMzy on 2011-12-08
```
sudo umount /media/[COLOR="Red"]mountpoint[/COLOR]
``` or ```
sudo umount /dev/[COLOR="Red"]sd**[/COLOR]
``` or ```
udisks --unmount /dev/[COLOR="Red"]sd**[/COLOR]
```

---

### Post by cortman on 2011-12-08
Thanks for the feedback! My problem was simply that I didn't realize I needed root to umount... One day I won't have to ask about these basic things...

---

