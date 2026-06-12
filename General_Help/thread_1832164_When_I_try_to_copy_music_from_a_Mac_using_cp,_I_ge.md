---
title: "When I try to copy music from a Mac using cp, I get a Input/Output error"
date: 2011-08-24
forum: General Help
---

### Post by andrewdonshik on 2011-08-24
How do i copy files from a mac. I either get Function not implemented if I use nautilus, or cp: cannot open `/home/andrew/.gvfs/brettdonshik on brett-donshiks-macbook.local/Music/iTunes/iTunes Media/Music/CMEA Honors Choir 2011/CMEA Honors Choir 2011/05 Sound the Trumpet_Encore_ Furaha.m4a' for reading: Input/output error, if I do it through terminal using cp.

---

### Post by aeiah on 2011-08-24
might be to do with the spaces in the name or some weird way its mounting your mac to the filesystem.

its probably easier to use rsync though.

in a terminal on your mac, do
```

rsync -aPn ~/path/to/the/directory/you/want/ username@ubuntu-machine-ip:~/path/to/destination/

```

this will do a simulated run. if it looks ok, remove the 'n' option flag and run it again. you'll need ssh enabled on your ubuntu machine for this.

---

### Post by andrewdonshik on 2011-08-24
I'll try that. 
I know that to get around the spaces, you put backslashes.

---

### Post by andrewdonshik on 2011-08-24
Thanks, It worked

---

