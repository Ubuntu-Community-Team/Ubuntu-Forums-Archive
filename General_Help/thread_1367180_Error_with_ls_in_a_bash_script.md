---
title: "Error with ls in a bash script"
date: 2009-12-29
forum: General Help
---

### Post by Andreas1 on 2009-12-29
why does the following script
```
#!/bin/bash

dir="~/testdir"
ls $dir

```
return
```
ls: ~/testdir: No such file or directory

```

while this one
```
#!/bin/bash

dir="$HOME/testdir"
ls $dir

```
works?

---

### Post by pbrane on 2009-12-29
try this:
```

!#/bin/bash

dir=~/testdir
ls $dir

```

The unquoted tilde ( ~ ) expands to $HOME but a quoted tilde does not. That is the rule.

[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_04.html")

look under **3.4.3 Tilde Expansion**

---

### Post by victor.zamanian on 2009-12-29
Variable expansion (starting $) occurs within quotation marks, while ~ is not expanded.

---

