---
title: "run script as if its non-relative directory"
date: 2010-01-12
forum: General Help
---

### Post by J V on 2010-01-12
I'm trying to run a python app from the main menu, but I currently need to proxy it through a bash script so as to set the cd correctly, is there any way to fix this?

---

### Post by J V on 2010-01-13
bump, need to change the cwd to current location in python, anyone?

---

### Post by slakkie on 2010-01-13
```

#!/usr/bin/env python

import sys
import os

print os.getcwd()
print sys.path[0]

```

---

### Post by J V on 2010-01-13
Edit: solved, thanks!

```
os.chdir(sys.path[0])
```

---

