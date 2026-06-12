---
title: "&quot;file not found&quot; on every option within &quot;Places&quot;"
date: 2010-11-19
forum: General Help
---

### Post by mrwaistcoat on 2010-11-19
Strange -  My only workaround is to select "computer" - this is now the only option on "places" that does not deliver a "file not found error"  

When I select computer I can still access the contents of my hard drive.

Any ideas ?

---

### Post by plucky on 2010-11-19
> **mrwaistcoat said:**
> Strange -  My only workaround is to select "computer" - this is now the only option on "places" that does not deliver a "file not found error"  

When I select computer I can still access the contents of my hard drive.

Any ideas ?

Try [This](http://ubuntuforums.org/showpost.php?p=10035020&postcount=3)

Good Luck

---

### Post by WorMzy on 2010-11-19
If that doesn't help, check the contents of ~/.gtk-bookmarks

This file is where all your non-system Places are stored. There should be one bookmark per line, they should all begin with file://, and they should be absolute paths (starting from /)

---

### Post by mrwaistcoat on 2010-11-19
Thanks Plucky, that worked a treat

It turns out my folders were trying to use Wine to open....

---

