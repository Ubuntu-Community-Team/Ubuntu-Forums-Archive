---
title: "apache 2 forbidden linked folder"
date: 2011-06-09
forum: General Help
---

### Post by iption on 2011-06-09
So after the last update, for some reason apache is no longer working with my linked folders.
Here is the problem:

lrwxrwxrwx dictionary -> /home/****/dictionary
drwxr-xr-x downloader

These are my two folders (i am the owner on both and on the containing files), on is the link the other one is a real folder. The real one I can access and the link I can not. 

I have the permissions inside the folders correct:
***w/dictionary$
total 68
drwxr-xr-x   .
drwxr-xr-x   ..
drwxr-xr-x   cache
drwxr-xr-x   classes
-rwxr-xr-x   config.php
drwxr-xr-x   configs

***/downloader$
total 172
drwxr-xr-x   .
drwxrwxrwx   ..
-rwxr-xr-x   download.log
-rwxr-xr-x   index.php
-rwxr-xr-x   links.php

And the real folder that is linked also has the right privileges:
drwxr-xr-x   dictionary

And now i don't understand why is this not working, and it used to work before.

---

