---
title: "Downloading from internet after adding local repo"
date: 2012-09-07
forum: General Help
---

### Post by m.r.karimi.j on 2012-09-07
Hey guys,
Last night I backed up my aptitude cache, located at /var/cache/apt/archives/ , and installed a fresh ubuntu 12.04.1.  Now I want to use it (it's 5.4 GBs!!!) and don't download the packages again.
Firstly, I generated a Packages.gz file by doing:
```
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz 
```and then I added this line at the beginning of my sources.list file:
```
deb file:/home/..../archives/ /
```and then ran
```
sudo apt-get update
```everything seems to be OK, but when I use apt-get install, it does not use my repository and downloads from internet. What do I do?!

---

