---
title: "Shell Scripting:: Check Free Disk Space"
date: 2009-08-04
forum: General Help
---

### Post by lightnb on 2009-08-04
How would I create a condition in my script to check for free disk space?

Like:

```

if(FreeSpace > 1GB)

# Do something

fi

```

---

### Post by warp99 on 2009-08-04
```
#! /bin/bash

space=`df /dev/xxx | awk 'NR==2 {print $4}'`

    if [ "$space" -gt 1048576 ] ; then
          echo "it works"
    fi

```

Replace xxx with the partition you're checking for free space.

---

### Post by lightnb on 2009-08-04
Thanks!

---

