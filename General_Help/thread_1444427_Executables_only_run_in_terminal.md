---
title: "Executables only run in terminal?"
date: 2010-04-01
forum: General Help
---

### Post by mohitd2000 on 2010-04-01
I was compiling some C source code into a .out file. But when I double-clicked on it, nothing happened. But when I run ```
./main.out
``` It runs just fine. What do I need to open the file as? I tested it with a simple program:
```
#include <stdio.h>

int main()
{
    printf("Hello World!\n");
    return 0;
}
```

---

### Post by john newbuntu on 2010-04-01
In nautilus, alter your edit->pref->behavior->executable text files to run it when they are opened.

---

### Post by mohitd2000 on 2010-04-01
Thanks, but that doesn't work. The file still doesn't so anything.

---

### Post by the yawner on 2010-04-01
It's a terminal program, hence why nothing happens when you try to run it. Unless you have a compiled program with a GUI. I.e. written with GTK etc.

---

### Post by geirha on 2010-04-01
When you double-click it, one of the options should be to «run in terminal». You'll have to choose that at least, but by default, the terminal closes as soon as the application ends, so it will be very brief. You can change that in the settings of gnome-terminal though. Under edit -> profile preferences there should be an option of what to do when the application ends. Set that to «keep terminal open» (or something along those lines).

Another option is to make a wrapper script and run that instead.

```
#!/bin/sh

./main.out
read

```

The read command will keep the script open until you hit enter.

---

