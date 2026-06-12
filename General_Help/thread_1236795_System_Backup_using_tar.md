---
title: "System Backup using tar"
date: 2009-08-10
forum: General Help
---

### Post by nmaster on 2009-08-10
Can you do this with OSX?  Just wondering.

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by quixote on 2009-08-11
You can use an OSX terminal just the same as an *nix terminal, so the sort-of answer is yes, you could do what that thread is talking about.

Only "sort of" though because OSX is not Ubuntu.  It's more closely related to BSD.  So you'd have to test everything first to make sure none of the commands behaved in unexpected ways under the specific OSX distro.

The other thing is that tar is no longer the only or even (IMHO) the best way to do backups. Using rsync to do incremental backups is the solution I like.  See, for instance, 

A Time Machine for every Unix: [http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

Making secure remote backups: [http://www.linux.com/archive/feature/113847?page=2](http://www.linux.com/archive/feature/113847?page=2)

Mike Rubel's thorough and early post on the topic: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by nmaster on 2009-08-12
thanks for the info.  i've just been thinking about how similar linux was to osx.  for example, i can't "lshw" on my friend's mac to find out what she has "under the hood" 

thanks for the info tho.

---

