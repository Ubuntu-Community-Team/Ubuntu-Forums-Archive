---
title: "problem formatting sources.list for new repository"
date: 2006-04-11
forum: General Help
---

### Post by Roobert on 2006-04-11
I'm trying to add my own ftp site to sources.list so I can use Lyx 1.4.0. I add the following line to the end of /etc/apt/sources.list:

```
## For Lyx binaries:
deb ftp://ftp.lyx.org/pub/lyx/bin/1.4.0/ubuntu/ 
```

Then running apt-get update gives the following error:

```
sudo apt-get update
E: Malformed line 34 in source list /etc/apt/sources.list (dist)

```

Line 34 corresponds to the last line in my sources.list, the line with the  pointer to the above ftp site.

How can I format the above ftp site so it will detect the deb files when I run Synaptic?

~ Roobert.

---

