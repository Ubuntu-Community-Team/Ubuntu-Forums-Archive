---
title: "TAR Not Working As Expected"
date: 2009-06-29
forum: General Help
---

### Post by dfxdeimos on 2009-06-29
I have a directory that has multiple subdirectories / files that I am trying to tar.
 
Say the structure is /etc/thing/stuff and I want to backup the stuff directory, I navigate to /etc/thing and type:
 
tar -cvvf stuff.tar stuff/
 
I end up with an emty stuff.tar file. It doesn't get the files from the stuff directory or any of its sub directories.
 
The documentation in general is absolute crap. Argh.

---

### Post by Slim Odds on 2009-06-29
This method works fine for me....

Are you sure you didn't do something wrong? Typo?

---

