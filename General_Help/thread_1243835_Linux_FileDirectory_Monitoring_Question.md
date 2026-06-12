---
title: "Linux File/Directory Monitoring Question"
date: 2009-08-18
forum: General Help
---

### Post by klaus0009 on 2009-08-18
Hi,
 
I'm interested writing or obtaining in a tool or script that will monitor:
 
a: when a file is created (e.g. - echo "New File" >> test.txt) 
and returns a fd or filename (ideally) and a timestamp 
 
 
b: when a file is deleted (e.g. rm test.txt)
and returns a fd or filename (ideally) and a timestamp
 
The purpose of the tool will be to monitor how long (time) a file exists (from creation to deletion) on a filesystem. 
 
It's the delta between create and delete I'm interested in.
 
I've checked inotifywatch, and some code found here:
 
[http://os.cqu.edu.au/docs/kernel-doc/Documentation/dnotify.txt](http://os.cqu.edu.au/docs/kernel-doc/Documentation/dnotify.txt) (which I was not able to successfully identify command parameters). 
 
inotifywatch gives a nice bulk report, but I didn't see where more granular data can be grabbed with it.
 
Thanks,

---

