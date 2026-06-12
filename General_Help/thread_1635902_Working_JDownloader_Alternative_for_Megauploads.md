---
title: "Working JDownloader Alternative for Megauploads?"
date: 2010-12-02
forum: General Help
---

### Post by drewsus on 2010-12-02
Hey all,
There is currently a bug with JDownloader in regards to downloading Megaupload files that keeps saying you need to reset your IP address. They download fine, one at a time, in my browser. I've looking into it and many, if not all, people are having this issue currently. 

So, what I am looking for is an alternative batch downloader for Megaupload links at the very least. 

Thanks,
Drew

---

### Post by akand074 on 2010-12-02
Works perfectly for Megaupload for me. Though I have a premium account, from what I can tell it doesn't seem that you do? I've never tried it without a premium account. But I have tried other hosts like hotfile, fileserve, etc. and it just downloads one at a time and then would make me wait 30 minutes or however long the particular hosts makes you wait before consecutive downloads.

---

### Post by drewsus on 2010-12-02
Other hosts work fine and this issue is for free users. someone uploaded a working fix to the megaupload plugin by hackin a .class file, but only 'supporters' can see the link to it on jdownloaders forums... Im not in the position to send them support atm.

---

### Post by akand074 on 2010-12-02
> **drewsus said:**
> Other hosts work fine and this issue is for free users. someone uploaded a working fix to the megaupload plugin by hackin a .class file, but only 'supporters' can see the link to it on jdownloaders forums... Im not in the position to send them support atm.

Hmm. Well I don't know how to fix the problem. But you can try Tucan. I used to use it before JDownloader but I found it rather buggy and its not very feature rich.

---

### Post by drewsus on 2010-12-02
Yeah I tried Tucan, but it doesnt seem to do anything at all.

---

### Post by segalion on 2011-01-13
can try [http://pyload.org/](http://pyload.org/)

Minihowto:
1. download oficial 0.4.3 ubuntu package from [http://pyload.org/download](http://pyload.org/download)
2. install it with
```
$sudo dpkg -i pyload-v0.4.3-noarch.deb
```
Probably ask you for initial configuration...
3. update to latest (tip) version at [https://bitbucket.org/spoob/pyload/downloads](https://bitbucket.org/spoob/pyload/downloads) (necesary to work with hosters).
```
$wget https://bitbucket.org/spoob/pyload/get/tip.zip
$unzip tip.zip
$sudo rm -R /usr/share/pyload
$sudo cp -R ./pyload /usr/share/pyload
```
4. start server with 
```
$pyLoadCore

```5. fun with your favorite browser at [http://localhost:8000/](http://localhost:8000/)

Thanks to pyload development group...

---

