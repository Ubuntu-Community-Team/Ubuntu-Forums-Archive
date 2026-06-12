---
title: "&quot;Run in Terminal&quot; doesn't run .bashrc"
date: 2012-01-17
forum: General Help
---

### Post by Raff1 on 2012-01-17
**I want to know why .bashrc is not run when running a script from nautilus with "Run in Terminal", and how I can add ifort to path (see below) independent of .bashrc.**

When opening a terminal to run a script, .bashrc is run initially. However, when I open the script from nautilus with "Run in Terminal" (or with a launcher), .bashrc is *not* run. This is a problem because I need ifort in my path, and ifort is added to path in .bashrc by the following line:

```
# Adding ifort to path at the beginning of every terminal session
source /opt/intel/bin/compilervars.sh intel64
```To verify that .bashrc is not run when running a script from nautilus I added the following line to the top of .bashrc:

```
#testing if .bashrc is run
echo $PATH > ~/Desktop/test.txt
```When opening a terminal, test.txt appears on the desktop, showing that the intel libraries (ifort)  is included in path. If I open a script from nautilus (or a launcher) with "Run in Terminal", test.txt does *not* appear on my desktop, indicating that .bashrc was never invoked.

So why isn't .bashrc run in this case, and what can I do to still add ifort to path in this case?

---

### Post by Raff1 on 2012-01-18
I found the solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1876075").

I had to include the following line in the top of the scripts I wanted to run in order to invoke .basrc:
```
#!/bin/bash -i
```

---

