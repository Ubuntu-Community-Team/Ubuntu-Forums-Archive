---
title: "gedit slow to start and end"
date: 2009-06-27
forum: General Help
---

### Post by imbjr on 2009-06-27
Just noticed that gedit can take a while to get up to speed in receiving text input, and slow to shut down, sometimes leading to the "not responding" dialog. However, once it has settled it was OK.

I suspect this has something to do with the fact that in its list of recently opened documents it had references to text files from a directory with 7000+ files in it. Once I had opened files from directories with far fewer files in them, enough to clear the list of references to the huge text file collection, gedit was much improved in responsiveness.

Anyone else experienced this?

---

### Post by imbjr on 2009-06-27
Ah, found the solution here:

[http://ubuntuforums.org/showthread.php?t=938208](http://ubuntuforums.org/showthread.php?t=938208)

Turn off gedit's file browser pane plugin. It probably choked when it saw all those text files.

---

