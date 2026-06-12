---
title: "wget"
date: 2010-06-03
forum: General Help
---

### Post by bullethead67 on 2010-06-03
im trying to use wget to download pdf files on instructables. I have loaded my cookies file and it does use them properly but it seems to try to get everything but the pdf files. i used the -Apdf option but it then only loaded a single index html file. the website wont let me get to the specific page with the pdf's

Heres the command i used i used it with the no parent option too with no luck

wget -nd --load-cookies cookies.txt -e robots=off -m --no-parent -A.pdf [http://www.instructables.com](http://www.instructables.com)

---

### Post by gzarkadas on 2010-06-14
Instructables requires to be a pro member to get pdfs; thus you must supply your user name and password, either by using the --http-user and --http-password options or, if you need more security, putting those info inside your .wgetrc file (see `man wget' for details) for this to work.

---

