---
title: "usage of &quot;find -mtime&quot;"
date: 2010-05-29
forum: General Help
---

### Post by pinoy43v3r on 2010-05-29
hi, i have a directory that contains Oracle archive files. this directory need to be updated and keep only files that are generated within the last 5 days. in this directory i have files dated from May 21 2010 up to today's date. so i used the command,

find /u2/oracle/archive -mtime +5 -exec rm {} \;


i was expecting to have files date from May 25 up to today only but when i listed the directory it contained files dated from May 23 up to today.

i was thinking how does the "find" command uses mtime such that it left files dated May 23 and May 24?

appreciate any help.

---

### Post by .nedberg on 2010-05-29
Today is the 29th. 5 days ago gives us the 24th.

But find rounds the value down.

From [http://ss64.com/bash/find.html](http://ss64.com/bash/find.html)
> A file 47.99 hours old will round down to 1 day, for this to have matched -atime +1, the file would have to have been accessed more than one day ago i.e two days ago or longer. To match a date range you can specify more than one test.

So +5 days will in fact give you all files more than (or equal to) 6*24 hours old.

That in effect will keep some files from the 23rd.

---

