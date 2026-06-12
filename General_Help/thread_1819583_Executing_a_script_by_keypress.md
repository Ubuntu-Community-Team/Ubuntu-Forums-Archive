---
title: "Executing a script by keypress"
date: 2011-08-06
forum: General Help
---

### Post by IQAndreas on 2011-08-06
Is there any way to map a shell script to run when you press a certain set of keys?

For instance, I may want to execute the following by pressing **CTRL+ALT+R** (if that key combination is not already taken)
```
compiz --replace --loose-binding ccp
```

Or perhaps I want to open the System Monitor by pressing **CTRL+ALT+DEL** (a la Windows)

---

### Post by realzippy on 2011-08-06
..try "xbindkeys"

[http://www.ubuntugeek.com/how-to-create-a-custom-keyboard-shortcut-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-custom-keyboard-shortcut-in-ubuntu.html)

---

### Post by xdominex on 2011-08-06
There certainly is! As root, create a file in the /bin folder. In my examples, this file will be called "comp-rep-ccp."
```

sudo touch /bin/comp-rep-cpp

```

Make it executable.
```

sudo chmod +x /bin/comp-rep-ccp

```

Open the file in gedit.
```

sudo gedit /bin/comp-rep-ccp

```

Now places the following in the file, then save it and exit gedit:
```

#!/bin/bash

compiz --replace --loose-binding ccp

```

After all of that, open your keyboard shortcuts application, create a new custom shortcut, set the command to "comp-rep-ccp," and pick a key combo for it! That should do the trick! Hope this helps.

---

