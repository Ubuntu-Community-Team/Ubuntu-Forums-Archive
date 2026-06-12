---
title: "Firefox 3.5.7 Bookmarks?"
date: 2010-01-31
forum: General Help
---

### Post by ManyBeers on 2010-01-31
Where does Firefox 3.5.7_64 keeps it's bookmarks on Ubuntu 9.10_64 bit.
I want to replace the default set with my Seamonkey_32 bit set from My Windows7_32 bit profile. I tried to import them but Firefox reports no "Program that contains bookmarks...." exists. Before doing this I mounted the Windows partition.

---

### Post by sgage on 2010-01-31
The bookmarks are kept in the profile directory as "places.sql".

---

### Post by Leppie on 2010-01-31
the bookmarks are in the profile folder:
```
~/.mozilla/firefox/{provile}.default/bookmarks.html
```

hope this helps

---

### Post by mdurham on 2010-01-31
> **sgage said:**
> The bookmarks are kept in the profile directory as "places.sql".

I think you meant places.sqlite

---

### Post by ManyBeers on 2010-01-31
> **Leppie said:**
> the bookmarks are in the profile folder:
```
~/.mozilla/firefox/{provile}.default/bookmarks.html
```

hope this helps

I don't know wherever I try to put my Seamonkey bookmarks when I start Firefox it always uses the default set. Maybe it's because i am trying to put 32 bit bookmarks in a 64 bit Firefox folder.

---

### Post by Leppie on 2010-01-31
> **ManyBeers said:**
> I don't know wherever I try to put my Seamonkey bookmarks when I start Firefox it always uses the default set.
could you post a screenshot of the folder you're trying to put the bookmarks into?

---

### Post by ManyBeers on 2010-01-31
> **Leppie said:**
> could you post a screenshot of the folder you're trying to put the bookmarks into?
Sure. ManyBeers profile folder.

---

### Post by sgage on 2010-01-31
Sometimes when there's a bunch of backup .json files in 'bookmarksbackup', Firefox will load them up. Delete them, and your places.sql will work.

---

### Post by Leppie on 2010-01-31
> **ManyBeers said:**
> Sure. ManyBeers profile folder.
did you use the profile manager to change the default location of your profile? [http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

your default profile directory should be hs5qjv8t.default

---

### Post by ManyBeers on 2010-01-31
> **sgage said:**
> Sometimes when there's a bunch of backup .json files in 'bookmarksbackup', Firefox will load them up. Delete them, and your places.sql will work.

I did that when I renamed bookmarks.html and installed my Seamonkey bookmarks.HTML file. It didn't help.

---

### Post by ManyBeers on 2010-01-31
> **Leppie said:**
> did you use the profile manager to change the default location of your profile? [http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

your default profile directory should be hs5qjv8t.default

The only thing I did with Profile Manager was create the ManyBeers profile. Isn't ManyBeers where I would put my Seamonkey bookmarks?

---

### Post by Leppie on 2010-01-31
> **ManyBeers said:**
> The only thing I did with Profile Manager was create the ManyBeers profile. Isn't ManyBeers where I would put my Seamonkey bookmarks?
if you created the manybeers profile with profile manager, that's where you should put the bookmarks.html file.

have you compared the contents of the two files?

---

### Post by sgage on 2010-01-31
Firefox 3.x keeps its bookmarks in your profile in places.sql, not bookmarks.html. If you copy/symlink an existing and working places.sql to your working profile, and it doesn't seem to show up when you look at your bookmarks menu, delete (or move) the .json files from bookmarkbackup, because sometimes FF will grab the latest backup for some reason. I haven't been able to figure out a pattern to this, but it happened to me and almost drove me nuts until I figured it out.

---

### Post by Leppie on 2010-01-31
if copying doesn't work, you could always use the import function ;)

---

### Post by ManyBeers on 2010-01-31
> **Leppie said:**
> if copying doesn't work, you could always use the import function ;)

I already referenced that in my first post.In fact I even mounted my Windows partition and then opened Firefox and tried to import then but it didn't find my Seamonkey profile.

---

### Post by ManyBeers on 2010-01-31
> **sgage said:**
> Firefox 3.x keeps its bookmarks in your profile in places.sql, not bookmarks.html. If you copy/symlink an existing and working places.sql to your working profile, and it doesn't seem to show up when you look at your bookmarks menu, delete (or move) the .json files from bookmarkbackup, because sometimes FF will grab the latest backup for some reason. I haven't been able to figure out a pattern to this, but it happened to me and almost drove me nuts until I figured it out.

Ok i have a copy of my desired bookmarks.html from Seamonkey. How do i get them where Firefox 3.5.7 will use them?

---

### Post by Leppie on 2010-01-31
> **ManyBeers said:**
> I already referenced that in my first post.In fact I even mounted my Windows partition and then opened Firefox and tried to import then but it didn't find my Seamonkey profile.
i didn't mean importing the seamonkey profile, but importing the seamonkey bookmarks. if your bookmarks are in the seamonkey's bookmarks.html you can use this file to import those bookmarks into ff.

---

### Post by lovinglinux on 2010-02-01
> **ManyBeers said:**
> Ok i have a copy of my desired bookmarks.html from Seamonkey. How do i get them where Firefox 3.5.7 will use them?

See the third paragraph on [this](http://lovinglinux.megabyet.net/?page_id=220#Backups-1).

---

### Post by ManyBeers on 2010-02-10
This [procedure]("http://kb.mozillazine.org/Lost_bookmarks_after_Firefox_3_upgrade") worked for me.
"Manual Deletion Method"

---

