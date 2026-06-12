---
title: "Text based copy program with nice looking progress"
date: 2010-02-05
forum: General Help
---

### Post by bakegoodz on 2010-02-05
I'm creating a script that others are going to use. In one section it copys a couple of gigs of thousands of file to one folder to another. I want a nice way to show progress. This is the best I can find: rsync -ah --progress /folder /otherfolder
It looks like garbage to me, but it is better then seeing nothing. Any suggestions?

---

### Post by falconindy on 2010-02-05
[http://www.theiling.de/projects/bar.html](http://www.theiling.de/projects/bar.html)

---

### Post by SecretCode on 2010-02-05
> **falconindy said:**
> [http://www.theiling.de/projects/bar.html](http://www.theiling.de/projects/bar.html)

Looks like that would work well for local copies.

How would you use it with rsync (or with some other command giving remote synchronisation with only differences sent)?

---

### Post by bakegoodz on 2010-02-05
Bar is useless, it can't handle folders. I guess it would be nice if you only needed to copy files in one folder.
Only need to copy a folder with sub folders to a network drive that is mounted as a standard linux folder, don't need the sync functions of rsync. cp is find from a technical perspective, but it doesn't give you an estimate when it done, which is something I need. I appreciate the help given so far though

---

### Post by SecretCode on 2010-02-06
I really expected rsync to provide this feature, when I started playing with it, but it seems like it doesn't.

If you feel like doing a bit of work, you could run rsync with --dry-run, get the list of the files, add up their sizes and work out the total, then manage your own progress bar during the real transfer.

I'm surprised that I can't find anyone who's done this already.

---

