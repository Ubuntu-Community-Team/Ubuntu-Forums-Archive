---
title: "Not sure why this script does this"
date: 2012-07-11
forum: General Help
---

### Post by wingnut2626 on 2012-07-11
I have this bash script:

```

#!/bin/bash
# This is a file to determine the top numbers in any given inventory 
# file.  It is assumed that the $filename is an inventory with each 
# item preceeded by a number.  If $howmany is undefined it will print
# a message stating such and will exit the program.

filename=$1
howmany=$2

sort -nr $filename | head -${howmany:=10}
clear 
echo ${howmany:?howmany is still undefined

# End of script

```

Shouldn't ${howmany:=10} set $howmany  to 10 for the rest of the script?  Instead of getting a 10 at the top of the screen after the clear, i have the default message.   Why?

---

### Post by Vaphell on 2012-07-11
value changed in the pipe doesn't get back to the main process.
Simply do that before *sort | head* line

---

### Post by spjackson on 2012-07-11
Because of the pipe, the "sort | head" line is executed in a sub-shell, which sets its own local version of $howmany. The $howmany of the parent shell is not changed. Instead you could do
```

howmany=$2
howmany=${howmany:=10}
sort -nr $filename | head -$howmany

```

---

### Post by sisco311 on 2012-07-11
Vaphell & spjackson beat me to it! :)

For more info check out BashPitfalls 008, BashFAQ 024 & [http://mywiki.wooledge.org/SubShell](http://mywiki.wooledge.org/SubShell)

---

### Post by wingnut2626 on 2012-07-13
thanks for the help

---

