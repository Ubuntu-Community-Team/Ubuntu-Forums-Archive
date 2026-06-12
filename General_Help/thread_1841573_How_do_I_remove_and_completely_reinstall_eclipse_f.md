---
title: "How do I remove and completely reinstall eclipse from scratch?"
date: 2011-09-09
forum: General Help
---

### Post by josephellengar on 2011-09-09
Every time I start Eclipse it creates a ton of junk all over my computer, including on my Desktop, flash drive, home folder, etc. I believe that this is from a failed installation that corrupted the computer and some preferences not that long ago. How would I remove the program including any stored settings, etc, that it may have so that I can reinstall it completely from scratch/cleanly? Thank you.

---

### Post by TeoBigusGeekus on 2011-09-09
```
sudo apt-get purge eclipse
```
to remove it, then
```
find ~/ -iname "*eclipse*"
```
to find any file or folder with the name eclipse in them.
View them and delete them if you like.

---

### Post by WorMzy on 2011-09-09
If you installed using apt-get or the software centre, there's unlikely to be anything wrong with the application's "system" files, so uninstalling/purging won't make any difference. The problem most likely lies with it's "user" files; that is, the config it created and place in your user's home folder when you first ran it.

Run Teo's find command to identify where the config was created (likely destinations include ~/.eclipse and ~/.config/eclipse), then either manually modify the config files, or delete them. If you delete them, a fresh set will be generated the next time you run eclipse.

---

### Post by josephellengar on 2011-09-09
Thanks! I was able to find and remove all of the config files (I think) so everything seems to be working right now. I had missed an eclipse folder in the .mozilla directory. Not sure why there was one there, but it seems to have solved the problem.

---

