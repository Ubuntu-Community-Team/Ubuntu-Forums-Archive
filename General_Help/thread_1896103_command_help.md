---
title: "command help"
date: 2011-12-16
forum: General Help
---

### Post by smasher40 on 2011-12-16
Hi, how can a list all files of my working directory, in order to show the full path of each file and it's name also???


Thanks very much

paulo

---

### Post by satish_j on 2011-12-16
you can use the find the command as
```

find <path to directory> -type f

```

---

### Post by lukeiamyourfather on 2011-12-16
If you need this for something other than a shell script there might be a better native way to do it. For example in Python you can walk directories to find files like this.

```

import os

for dirname, dirnames, filenames in os.walk('.'):
    for subdirname in dirnames:
        print os.path.join(dirname, subdirname)
    for filename in filenames:
        print os.path.join(dirname, filename)

```

Other languages like Java, C, Ruby, and so on have similar methods. Disregard if you're using it for a shell script or just in the shell. :)

---

