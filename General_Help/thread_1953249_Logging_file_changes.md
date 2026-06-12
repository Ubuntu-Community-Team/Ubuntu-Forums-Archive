---
title: "Logging file changes"
date: 2012-04-05
forum: General Help
---

### Post by Idefix82 on 2012-04-05
Does Ubuntu log somewhere all changes made to files, so that I can see what file was changed at what time? If that doesn't happen by default, is there a daemon that can be asked to watch a particular folder and log all changes with time stamps?

---

### Post by erind on 2012-04-05
There is a nice little tool - **inotifywait **(from **inotify-tools** package), that does folder/file monitoring. Its man pages are quite helpful too:

[http://linux.die.net/man/1/inotifywait](http://linux.die.net/man/1/inotifywait)

---

### Post by Idefix82 on 2012-04-06
Perfekt - thank you!

---

