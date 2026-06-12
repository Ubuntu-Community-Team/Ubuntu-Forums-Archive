---
title: "Apt-fast"
date: 2010-12-06
forum: General Help
---

### Post by COKEDUDE on 2010-12-06
Has anyone ever tried tried Apt-fast? What it is claiming is quite intriguing. It is claiming that it can download 26x faster than apt-get. 

[http://www.sourceslist.eu/installare-software-tramite-repository/apt-fast-and-axel-roughly-26x-faster-apt-get-downloads/](http://www.sourceslist.eu/installare-software-tramite-repository/apt-fast-and-axel-roughly-26x-faster-apt-get-downloads/)

---

### Post by tgalati4 on 2010-12-06
I'll wait until others use it and post their results.  I would hate to mangle a working system with something new/untried.

---

### Post by COKEDUDE on 2010-12-06
> **tgalati4 said:**
> I'll wait until others use it and post their results.  I would hate to mangle a working system with something new/untried.

Yea thats what I was thinking. I didn't even see it in the debian repository. They usually have way more software than the ubuntu repository.

---

### Post by sgosnell on 2010-12-06
I've tried it, and it works, sort of.  It splits the downloads into multiple downloads, up to 4 or 5, to get more performance from the server.  I found that the first ones all ran very quickly, but the last one almost always stalled, and the total download time was about the same as with standard apt-get.  I used it almost exclusively for some time, but I got tired of seeing the final segment of the download sit there for many seconds doing nothing. It seems to work better for large files, not so well when there are lots of relatively small files to get.  It's a good theory, but not well executed.  I gave up on it and now just use apt-get.

---

### Post by tgalati4 on 2010-12-06
What did speed up the install process was cleaning up the dpkg database.  There's a thread that describes what steps are required.  Basically, a lot of time is spent rereading the dpkg database after every package is installed.  This causes fragmentation of the database and slow release of the program.  That is why synaptic takes a while to load and refresh.

Another speed-up (that may be coming soon) is downloading delta-packages.  Upgrades currently replace all files associated with a package.  Future upgrades will only change the files that actually contain code changes.  This will reduce downloading redundant/unchanged code and save time by only installing stuff that actually has changed.

---

