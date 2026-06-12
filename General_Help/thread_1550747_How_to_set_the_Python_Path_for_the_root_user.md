---
title: "How to set the Python Path for the root user?"
date: 2010-08-11
forum: General Help
---

### Post by bfrederi on 2010-08-11
How do I set the PYTHONPATH for the root user only? Or at least add to the python path for the root user? I need to read from the /var/log/apache2/access.log in my python script, so I need to use sudo for my script to be able to read from it.

I tried setting the PYTHONPATH in /root/.bashrc but that didn't work. I don't want to use a .pth file because I don't want the directory to be on the path for all users due to import collisions. Any ideas?

---

### Post by surfer on 2010-08-11
you could set the path inside the script itself:

```

#!/usr/bin/python

import sys

sys.path.append('/tmp')
print sys.path


```

---

### Post by bfrederi on 2010-08-11
If I don't find a better option, I will go with that. I was hoping to not have to embed the path in the script, because then I will have to change the script for every different server/path I deploy it on. This script will live on different paths on multiple servers and be deployed through subversion, so that's not an ideal solution.

---

### Post by DaithiF on 2010-08-11
add the path in the script, but make it dynamic by using the __file__ variable, so that it works whereever the script gets deployed.

```
sys.path.append(os.path.abspath(os.path.dirname(__file__)))
```

---

### Post by bfrederi on 2010-08-11
Ah yes, I forgot about that trick. I use that in my Django settings file. Thanks!

---

### Post by bfrederi on 2010-08-11
> **DaithiF said:**
> add the path in the script, but make it dynamic by using the __file__ variable, so that it works whereever the script gets deployed.

```
sys.path.append(os.path.abspath(os.path.dirname(__file__)))
```

This fails if you make the script executable and symbolically link it into /usr/local/bin. You will get "/usr/local/bin" as the path to append. Any suggestions for a workaround for that instance?

---

### Post by DaithiF on 2010-08-11
check out os.path.realpath to resolve to the linked script rather than the link itself.

---

### Post by hasinasi on 2012-09-26
I realize this thread is old. Nevertheless, I am adding to it, as it shows up high in the search results corresponding to this topic.  

I had a similar problem: I was trying to import a library I had created somewhere in my home folder. I had added its folder to $PYTHONPATH in "/root/.bashrc", but it still did not find the library. I checked sys.path, and sure enough, the path was there.  

The problem, however, turned out to be that the library in my home folder did not have "execute" permissions for the root user (specifically, it was the *.pyc file belonging to the library). After 'chmod -x' for the file, it works without any problems.

---

