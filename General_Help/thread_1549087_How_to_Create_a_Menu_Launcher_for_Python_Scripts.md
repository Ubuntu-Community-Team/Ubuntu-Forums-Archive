---
title: "How to Create a Menu Launcher for Python Scripts?"
date: 2010-08-09
forum: General Help
---

### Post by Iteria on 2010-08-09
I'm running lucid with gnome and I have this little python program and I want to launch it from the menu, instead of the command line which is what I'm doing now. I can't get it to work at all. The commands I gave it were:

cd /path/to/script && ./script.py

The menu launcher doesn't seem to like cd, so I'm at a lost as to what to do since I have to execute the script from the directory (to my knowledge. Correct me if I'm wrong.).

---

### Post by DaithiF on 2010-08-09
> **Iteria said:**
> ... since I have to execute the script from the directory (to my knowledge. Correct me if I'm wrong.).
that'll depend on the particular python script, but yes, its quite possible.  (Just try running it from a different directory to check)

if you do need to be in the same directory, then create a shell script and run that script from your launcher entry.

script to contain something like:
```
#!/bin/sh
cd /some/dir
./script.py

```

---

### Post by Iteria on 2010-08-09
That worked! Thank you so much.

---

