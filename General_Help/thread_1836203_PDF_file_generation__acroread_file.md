---
title: "PDF file generation / acroread file"
date: 2011-08-30
forum: General Help
---

### Post by lory on 2011-08-30
Hi
I have a tax program (reinstalled) that should print pdf files. However, if gives an error because it cannot find file and path to file "acroread %1"
Last year I had the same problem and I solved by installing acroread and giving the path ot the program:
sudo apt-get install acroread
and then in the program I have inserted "/usr/bin/acroread %1"

But this time I cannot install acroread:

sudo apt-get install acroread
reading package list ... done
Building dependensy treee
Reading state information... Done
E: Unable to locate package acroread

What might be the problem?

Thanks

---

### Post by Enigmapond on 2011-08-30
This might prove helpful....just googled..

[http://techcolleague.com/2011/02/install-adobe-acrobat-reader-on-ubuntu/](http://techcolleague.com/2011/02/install-adobe-acrobat-reader-on-ubuntu/)

You need to add the PPA prior to installing.

---

