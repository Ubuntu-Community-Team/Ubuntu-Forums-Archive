---
title: "apt orphans?"
date: 2009-11-13
forum: General Help
---

### Post by krakenfury on 2009-11-13
Is there and apt-get command that I can use to check for orphans?  I couldn't find anything in the man pages except for 'check' and that doesn't seem to find anything.  I know there are libraries I have installed that have remained after I removed binaries.  I know how to use 'autoremove' now, but now I can't remember all the different things I've tried out and removed.

---

### Post by diesch on 2009-11-13
*deborphan* or *debfoster* (both not installed by default) may be what you are looking for.

---

### Post by seeker5528 on 2009-11-13
If you install aptsh, then you could either run aptsh then type the command 'orphans' or 'orphans-all', but orphans all may have a lot of output so it does allow you to pipe the out put to less:

```
orphans-all | less
```

Or execute aptsh with the '-x' command line option:

```
sudo aptsh -x orphans-all | less
```

While aptsh is running you can type 'help' to view the contents of the man page.

Later, Seeker

---

### Post by krakenfury on 2009-11-13
Thanks!  I'll try these out.

---

### Post by arnab_das on 2009-11-13
this is the thread for all that and more:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

