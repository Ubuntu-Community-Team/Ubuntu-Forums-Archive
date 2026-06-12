---
title: "python: kill traceback reporting from within code?"
date: 2011-03-28
forum: General Help
---

### Post by d3v1150m471c on 2011-03-28
Is there a way to turn off python's traceback reporting to the terminal for the duration of it's execution? IE
```

import somemodule
traceback(off)
# yes, i just made that up :)

```
edit:
lol i always do this...anyways, if anyone wants to know setting the variable sys.tracebacklimit to 0 will supress all traceback output.

```

#!/usr/bin/python
sys.tracebacklimit = 0

```

---

