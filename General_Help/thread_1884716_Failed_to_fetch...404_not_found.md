---
title: "Failed to fetch...404 not found"
date: 2011-11-21
forum: General Help
---

### Post by Jammanuser on 2011-11-21
Hello,
I am having trouble installing various packages in Ubuntu 9.10. The error I keep getting says something like:

> 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz)  404  Not Found

with maybe a few differences in the URL with each different one. But each one seems to be located at a subdirectory of [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu).

I added the line "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main" to the end of my /etc/apt/sources.list, but that didn't fix the errors.

Any idea how I can resolve the 404 not found error with packages on that server?

Thanks in advance.

---

### Post by bkratz on 2011-11-21
Karmic went eol in April of 2011.  See

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Jammanuser on 2011-11-21
> **bkratz said:**
> Karmic went eol in April of 2011.  See

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Well, I'm planning to upgrade it to the latest version of Ubuntu as soon as I resize the partition its on, since I don't have enough free space on the partition right now to upgrade it. Incidentally, I don't see what that has to do with my problem though...:D

Cheers. :popcorn:

-Jam Man

---

### Post by bkratz on 2011-11-21
the repositories were moved to old releases at that time. See this page

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

about half way down the page it shows how the sources list can be changed.

---

### Post by Jammanuser on 2011-11-21
> **bkratz said:**
> the repositories were moved to old releases at that time. See this page

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

about half way down the page it shows how the sources list can be changed.
Ok, so is that the complete sources.list which I'm supposed to replace the current content with, or do I just add that code to the end of my sources.list?

Thanks for the help.

---

### Post by bkratz on 2011-11-21
I honestly don't know whether Karmic has actually been moved yet, it took a long time for some earlier versions, but you would have to change each entry of  your /etc/apt/sources.list to point to old releases. Here is where the old releases are available.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

I have never actually done this myself so use caution. Why not upgrade to at least 10.04 (that is where I went for now) don't like the newer ones. It is good until April 2013.

---

### Post by Jammanuser on 2011-11-21
> **bkratz said:**
> I honestly don't know whether Karmic has actually been moved yet, it took a long time for some earlier versions, but you would have to change each entry of  your /etc/apt/sources.list to point to old releases. Here is where the old releases are available.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

Well, I think it has moved, because on closer examination of my terminal output, it seems there are other subdomains of ubuntu.com which is producing the 404 Not Found error as well as us.archive, for example:

> 
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
  404  Not Found [IP: *deleted*]


> 
I have never actually done this myself so use caution. Why not upgrade to at least 10.04 (that is where I went for now) don't like the newer ones. It is good until April 2013.
I am planning to upgrade to 10.04, but like already mentioned in my previous post, I do not have enough space right now to upgrade, so I'm going to have to resize my partitions to make some more free space I can give to my ubuntu partition.

---

