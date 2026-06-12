---
title: "tail flag for multiple files"
date: 2010-01-26
forum: General Help
---

### Post by chipmunk02115 on 2010-01-26
In Ubuntu 6.06, /usr/bin/tail could be executed with a simple -# flag (instead of standard -n #) to get the last # lines of the files in command argument. /usr/bin/head worked the same way with -# flag to get the first # lines of the files in command argument.

Starting Ubuntu 8.04 and now Ubuntu 9.10, /usr/bin/tail returns the following error message when executed with more than 1 text file in argument:

[FONT=Fixedsys]me@computer-ubuntu9.10:~/$ tail -3 file1.txt file2.txt
tail: option used in invalid context -- 3
[/FONT]
and yet, the -3 flag works for a single text tile,
[FONT=Fixedsys]
me@computer-ubuntu9.10:~/$ tail -3 file1.txt
[/FONT]line n-2
line n-1
line n

Ironically, /usr/bin/head flags work unchanged in Ubuntu 9.10 from Ubuntu 6.06. 
Again, I know full well that "tail -n 3 file1.txt file2.txt" works - but I found the asymmetry of tail and head flags for multiple files a little annoying.

So my ad hoc solution to make head and tail flags (across >1 files) symmetric is to replace with the /usr/bin/tail in my current Ubuntu 9.10 installation with /usr/bin/tail from Ubuntu 6.06 which works on multiple files.

I thought it would be useful to post my fix in case someone else noticed this head and tail flag asymmetry ever since Ubuntu 8.04. Far as I can tell, this does not break anything else in the system.

---

