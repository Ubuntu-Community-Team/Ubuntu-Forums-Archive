---
title: "Configure .screenrc file to open screen terminal in specific place"
date: 2011-10-29
forum: General Help
---

### Post by Closrapexa on 2011-10-29
I have a .screenrc configuration that opens several screen terminals upon initiation of screen; one for "general" use, one for playing music, etc. How can I configure one of the windows to open in a specific location on startup?

---

### Post by Toz on 2011-11-04
By "specific location" do you mean a location on your file system or a location on the screen (in case of a split screen setup)? If the latter, perhaps post #2 from this thread will help ([http://ubuntuforums.org/showthread.php?t=1856460&highlight=screenrc]("http://ubuntuforums.org/showthread.php?t=1856460&highlight=screenrc"))

---

### Post by Closrapexa on 2011-11-07
No, a specific location on my computer.

---

### Post by Toz on 2011-11-07
Create a bash file that simply cd's to a location and create a window with that bash file:
```
$ cat ~/bin/work
#!/bin/bash
cd /my/location
```
...then as a part of .screenrc
```

.....
screen -t email 1 alpine
screen -t irssi 2 irssi
screen -t work  3 work
.....
```

---

