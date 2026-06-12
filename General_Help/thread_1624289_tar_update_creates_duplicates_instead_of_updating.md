---
title: "tar update creates duplicates instead of updating"
date: 2010-11-17
forum: General Help
---

### Post by Jonny87 on 2010-11-17
I've tried using a script to run incremental backups. The idea was to use the update switch to just update the files in the .tar instead of creating new ones. However it seems to have created duplicate files in the tar instead of just updating them (refer to screenshot). Is this normal?

Here is the command in the script;
```
tar -uvpf /home/jonny/.BackUps/Updating/Documents.tar /home/jonny/Documents
```

Is there a way stop this but still have them update to the latest version?

---

### Post by andrewc6l on 2010-11-17
According to the manpage, that's what -u is supposed to do:

-u
--update
Append the named files if the on-disk version has a 
modification date more recent than their copy in the 
archive(if any).  Does not work on quarter-inch tapes.

I think this is a case where tar's history as a Tape ARchiver is showing. There's no easy way inside tar to insert a bigger file. 

GNU tar has a way to do incremental backups; see here:
[http://www.gnu.org/software/tar/manual/html_section/Incremental-Dumps.html](http://www.gnu.org/software/tar/manual/html_section/Incremental-Dumps.html)

---

