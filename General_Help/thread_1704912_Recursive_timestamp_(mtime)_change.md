---
title: "Recursive timestamp (mtime) change"
date: 2011-03-11
forum: General Help
---

### Post by qwerdy on 2011-03-11
=) Hello,

I store a lot of pictures on a ext3 partition, and use a php web gallery. (without database)

The gallery has the option to sort files and folders by date, but as I have a lot of subfolders, the timestamp on the "top-level-folders" never change, thus making the sort option worthless.

_Is it a way to make recursive timestamp change?_ 
So that when a new file is added in a sub directory, the timestamp changes all the way to the top.


Or is the answer to use a database based gallery? But then it would need to scan for changes periodically. Cause i upload images by a file manager.(not web upload).

---

### Post by dcstar on 2011-03-12
> **qwerdy said:**
> =) Hello,

I store a lot of pictures on a ext3 partition, and use a php web gallery. (without database)

The gallery has the option to sort files and folders by date, but as I have a lot of subfolders, the timestamp on the "top-level-folders" never change, thus making the sort option worthless.

_Is it a way to make recursive timestamp change?_ 
So that when a new file is added in a sub directory, the timestamp changes all the way to the top.


Or is the answer to use a database based gallery? But then it would need to scan for changes periodically. Cause i upload images by a file manager.(not web upload).

The command "touch" will update any folder/file with the current timestamp.

---

