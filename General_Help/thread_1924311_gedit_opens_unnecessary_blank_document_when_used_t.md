---
title: "gedit opens unnecessary blank document when used to open a file as root"
date: 2012-02-12
forum: General Help
---

### Post by tomluft on 2012-02-12
Are there any other users annoyed by [this bug]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/880038")?

Did someone maybe even find a solution yet? It sometimes really is a pita, especially when you just want to quickly edit some files and you get an annoying save-prompt for this annoying blank annoy-file.

---

### Post by jerrrys on 2012-02-12
Thats a bug report for 12.04.  Is that what your running?  If so, your post would be better placed in "Ubuntu +1 (Precise Pangolin)" forums; as most of us do not run it.

---

### Post by bluexrider on 2012-02-12
> **tomluft said:**
> Are there any other users annoyed by [this bug]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/880038")?

Did someone maybe even find a solution yet? It sometimes really is a pita, especially when you just want to quickly edit some files and you get an annoying save-prompt for this annoying blank annoy-file.

recommended using gksudo instead of sudo. This has been the recommendation 

GUI=gksudo
CLI=sudo

Opening gedit via the command line allows the user to take advantage of  several options unavailable from the GUI menu. If a path is not included  in the startup command, gedit will look for the file in the current  directory. If the file is not found, gedit will open a blank file with  the file name entered on the command line: 
[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit)

---

### Post by Aliarse on 2012-02-12
> **tomluft said:**
> Are there any other users annoyed by [this bug]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/880038")?

Yep i get this too, always opens up an "untitled-document" every time

---

### Post by bluexrider on 2012-02-12
> **jerrrys said:**
> Thats a bug report for 12.04.  Is that what your running?  If so, your post would be better placed in "Ubuntu +1 (Precise Pangolin)" forums; as most of us do not run it.
I would suppose it could go either way......

Is it a bug or is it default by design?

---

