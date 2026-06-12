---
title: "Cannot launch compiled C++ program in Code Blocks"
date: 2011-07-21
forum: General Help
---

### Post by ausairman on 2011-07-21
I initially posted this on the Code::blocks forum but they seemed to think it has nothing to do with their software, and that it's a GDB issue, whatever that means.

For some reason when I hit "run" in code::blocks nothing happens. The program compiles fine, it just doesn't launch the console. I have the following under "Terminal to launch console programs":

```
gnome-terminal -t $TITLE -x
```

when I run the program in Debug mode it launches fine though, although it says the following before running the program:

```
warning: GDB: Failed to set controlling terminal: Operation not permitted
```

..I have searched and searched but all I could find was the proposed solution to add the above command into "Terminal to launch console programs" but all that did was move the program from some white console into the black one...

---

