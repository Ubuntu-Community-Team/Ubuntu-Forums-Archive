---
title: "Downloading entire directory with wget"
date: 2009-07-23
forum: General Help
---

### Post by FaNaTiX on 2009-07-23
Hi All,

I've been using Ubuntu for a good number of years now, however this is my first time posting to the fourms, and like many, I've come looking for answers. :P

I need to get a specific set of files from a website at a set interval. I know this can be accomplished with cron and wget, however I'm unsure on exactly how to tweak it to my needs.

I'm looking to retrieve meteorological data for use with GEMPAK/NAWIPS from a website. The data is buried deep in tons of other directories. When I use
```
wget -e robots=off -r -l1 --no-parent -A N0R* http://website.tld/directory1/directory1/etc
```
Wget successfully downloads all files that begin with "N0R" to the directory I was in while in the command line. However if I run it from my home directory, it would completely mirror the entire directory structure of the website I'm pulling data from. That is to say it would make something similar to "/home/administrator/dataiwanttouse/website.tld/directory1/directory2/etc" with all of the files in the website's .../directory2/etc located in my .../directory2/etc.

My question is... how should I go about getting wget to put the files in ../dataiwanttouse/ instead of creating an exact mirror of the site?

Thanks in advance!

---

### Post by wojox on 2009-07-23
Try -nd  or  --no-directories  
With this option turned on, all files will get saved to the current directory.

---

### Post by FaNaTiX on 2009-07-23
Worked like a charm. :)
Thanks!

---

