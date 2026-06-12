---
title: "How to get inotify to watch subdirectories..."
date: 2010-10-07
forum: General Help
---

### Post by XtremeGamer99 on 2010-10-07
Hello,

I run a torrent box that automatically downloads TV shows. When this happens, sometimes a new directory is created.

I wanted to use inotify to watch these directories for when a file is moved to it (meaning the download is done) and to send a command. However, the fact that inotify cannot automatically watch subdirectories leaves me in a  sticky situation. Every subdirectory needs to be added manually, and since these subdirectories are dynamic (can come and go without warning) I need to something to watch for -them-, and add them to the inotify program.

Is there a way to do this without running a script every 5 minutes to add any new directories? because that will not work...

---

