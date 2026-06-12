---
title: "find command"
date: 2011-02-03
forum: General Help
---

### Post by mmxm45 on 2011-02-03
If I want to list all files of a particular extension would I use the find command? for example,
find -name '*.txt'
Would this list all text files?
Thanks

---

### Post by ratcheer on 2011-02-03
Almost. You need to specify a path from which to start the search. Very often, "." is used to specify the current working directory. So, some examples would be:

find . -name "*.txt"  -  to start at the current working directory

find /opt -name "*.txt"  -  to find them in /opt and its subdirectories

find / -name "*.txt"  -  to find them anywhere under root

Tim

---

