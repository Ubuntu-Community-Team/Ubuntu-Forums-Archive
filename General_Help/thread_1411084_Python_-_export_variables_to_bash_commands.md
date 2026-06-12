---
title: "Python - export variables to bash commands"
date: 2010-02-19
forum: General Help
---

### Post by d3v1150m471c on 2010-02-19
I created variables in python and would like to be able to incorporate those into bash commands that will be mixed into the script.
Example:
```

name=raw_input("Type your name and press ENTER: ")
import os
os.system( echo "name")

```

Of course this doesn't actually work, but i think you get an indication of what I am trying to do. Any advice would be appreciated.

---

### Post by d3v1150m471c on 2010-02-19
Update. Okay got it

```

name=raw_input('d3v11')
import os
os.system('echo "$name"')

```

---

