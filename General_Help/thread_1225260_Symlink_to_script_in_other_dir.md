---
title: "Symlink to script in other dir"
date: 2009-07-28
forum: General Help
---

### Post by dilomo on 2009-07-28
Hi,

I was wondering if it is possible to create a link to a python script that loads other files from the same directory in which it is. When I create a link in different folder the script runs but does not load the other files needed. Why is that? How can I solve the problem?

---

### Post by DaithiF on 2009-07-28
Hi,
imports from the script directory should work ok in python, regardless of which directory you run from, but if the script is also opening files from that directory and using relative paths then you will have a problem when running from a different directory.

one solution would be to create a wrapper script rather than a symlink.  for example:

#!/bin/sh
cd /path/to/script
python script.py

hope this helps
d

---

### Post by dilomo on 2009-07-28
> **DaithiF said:**
> Hi,
#!/bin/sh
cd /path/to/script
python script.py

hope this helps
d

Yeah that helped. Thank you very much man!

---

