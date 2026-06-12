---
title: "How can you now see Firefox bookmarks from a mounted partition from the CL?"
date: 2009-08-16
forum: General Help
---

### Post by DrCR on 2009-08-16
I used to be a "serial installer" installing many distributions natively to check them out. Less so nowadays, and I'm now cleaning up my HDD. Before I blow away a partition though, I like to quickly peruse over the lightly used install to see if there's any data I want to keep.

How do I check to see if there's any bookmarks from the mounted install that I want to keep now that Firefox is apparently using a database to store bookmarks?

Before, the following would do the trick. What now with the new DB? Or will the following actually continue to work?
```
lynx /mnt/sda7/home/drcr/.mozilla/firefox/blah.default/bookmarks.html

```

DrCR

---

### Post by dcstar on 2009-08-16
> **DrCR said:**
> I used to be a "serial installer" installing many distributions natively to check them out. Less so nowadays, and I'm now cleaning up my HDD. Before I blow away a partition though, I like to quickly peruse over the lightly used install to see if there's any data I want to keep.

How do I check to see if there's any bookmarks from the mounted install that I want to keep now that Firefox is apparently using a database to store bookmarks?

Before, the following would do the trick. What now with the new DB? Or will the following actually continue to work?
```
lynx /mnt/sda7/home/drcr/.mozilla/firefox/blah.default/bookmarks.html

```

DrCR

Firefox has an Export Bookmarks function, use it.

---

### Post by P4man on 2009-08-16
not really an answer to your question, but you can avoid the dilemma by installing xmarks. It lets you synchronize firefox (and other browsers) bookmarks (and if you want, passwords) with the cloud for all your machines and installs. Its about the first thing I download on any install. 

[http://www.xmarks.com/](http://www.xmarks.com/)

---

### Post by DrCR on 2009-08-16
dcstar, that doesn't do me any good -- I'm not booted into that install.

P4man, I don't like to live in the clouds. Guess you could say I'm a down to earth kind of guy lol. :) But seriously, I don't dig the cloud in general. My personal choice.


I just want to take a quick glance at the bookmarks. This used to be incredibly easy. Is there a way I can open the database with a simply command i.e. something like "cat bookmarkdatabase"?

Thanks,
DrCR

---

