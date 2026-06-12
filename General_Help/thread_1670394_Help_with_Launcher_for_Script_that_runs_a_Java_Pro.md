---
title: "Help with Launcher for Script that runs a Java Program"
date: 2011-01-18
forum: General Help
---

### Post by kendoori on 2011-01-18
I want to create a launcher that will excecute a java program that has no UI. It normally just runs in terminal..

Assuming that I'm in the right directory, if I run the following from terminal, the program runs fine:

```
java -classpath lib/config.jar:lib/logi.crypto1.1.2.jar config.bcu.Bcu
```

I've created a script as follows called bcu.sh:

```

#!/bin/bash
cd arecov/config
java -classpath lib/config.jar:lib/logi.crypto1.1.2.jar config.bcu.Bcu

```

If I run the script from terminal, by entering the directory, then sh bcu.sh it works correctly. Terminal pops up, executes the commands.

If I point a launcher to this script, it appears to execute, but the terminal window is hidden. How can I get the launcher to run the script, and have the execution of it appear visible in terminal?

---

