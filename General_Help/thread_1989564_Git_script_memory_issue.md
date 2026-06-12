---
title: "Git script memory issue"
date: 2012-05-28
forum: General Help
---

### Post by Jeroen De Dauw on 2012-05-28
When running the following python git script, it builds up memory usage and after a few minutes hits 6GiB after which my machine goes into swap and hangs.

[https://github.com/johl/subtree.py/blob/master/subtree.py](https://github.com/johl/subtree.py/blob/master/subtree.py)

The person who wrote this script can run it just fine on his MacOS X.

I tried limiting my git memory usage to something reasonable, but even after changing a dozen or so settings, the script is still behaving the exact same way :/

The git process itself is the thing taking all of the memory, not the python script.

Git itself works just fine for everything else I'm doing, and I have version 1.7.9.5 on Ubuntu 12.04 x64 running KDE.

Anyone an idea why it might be consuming so much memory, and more importantly, how to limit it, so I can actually use the script? :)

---

