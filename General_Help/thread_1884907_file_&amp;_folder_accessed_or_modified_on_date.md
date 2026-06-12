---
title: "file &amp; folder accessed or modified on date"
date: 2011-11-22
forum: General Help
---

### Post by techbrainless on 2011-11-22
Hi All ,
Is there any way to find any folder or file which has been accessed or modified on specific date

for example I want to get all the  files and folders which have been accessed or modified on date 11/11/2011

---

### Post by aeiah on 2011-11-22
well, access times (which includes modified times) are stored but i dont think the history is, so if the file has been accessed on 11/11/11 but also accessed since then, it wouldn't show an access time of 11/11/11

i think the proper way is to use find and the -atime flag but using specific dates seems fiddly. it doesnt look like you can specify the date on the command line because the -newer flag expects a file. a comment from [here](http://www.cyberciti.biz/faq/howto-finding-files-by-date/) talks about creating two date files (comment 14) to span a date range

if its easy to calculate, you could use the atime flag to find files accessed *n* days ago, though. today, 11/11/11 was 11 days ago, so:

```

find . -daystart -atime 11

```

if you want modify time and not access time, use -mtime instead of -atime. 

the dot in 'find . -daystart -atime 11' is shorthand for your present location (typically your home dir if you've just opened the terminal. it'll fine files recursively but obviously won't search elsewhere on your filesystem. if you want to search the whole thing (ie, root and any attached drives) use 'find / -daystart -atime 11' or any other location of your choosing

---

