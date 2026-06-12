---
title: "Using output from awk"
date: 2011-02-06
forum: General Help
---

### Post by whatthefunk on 2011-02-06
I'm using awk to read lines of text from files based on user input.  My code looks like this:

```
awk 'NR==4' "/home/username/folder/$variable"
```

This code displays the fourth line of text from the named file.  In this case, the fourth line of text is a new path.  I want to then move a different file to this new path but I can't figure out the correct syntax to do this.  Can anybody help me out?
Thanks

---

### Post by gmargo on 2011-02-06
```

#!/bin/sh
destfile=$(awk 'NR==4' "/home/username/folder/$variable")
if test -n "$destfile" ; then
     mv SOURCE_FILE "$destfile"
fi

```

---

### Post by whatthefunk on 2011-02-06
Got it.  Thanks gmargo.

---

