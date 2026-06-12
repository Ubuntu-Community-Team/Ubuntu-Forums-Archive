---
title: "Downloading files within a direcotry"
date: 2011-02-09
forum: General Help
---

### Post by diablo69er on 2011-02-09
I heard you can use wget to download all files within a given folder.  Every time I try though the only files I get are html files.  I am trying to download a good bit of .mov files.

What could I be doing wrong here?

---

### Post by oracle2b on 2011-02-09
wget -r -c -np -e robots=off --random-wait <Insert URL here>

or 

wget -m -r -np robots=off [http://some-website.com/files/](http://some-website.com/files/)

---

