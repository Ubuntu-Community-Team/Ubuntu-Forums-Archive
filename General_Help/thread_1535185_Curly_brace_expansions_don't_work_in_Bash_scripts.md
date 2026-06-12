---
title: "Curly brace expansions don't work in Bash scripts"
date: 2010-07-20
forum: General Help
---

### Post by CosineQuaNon on 2010-07-20
I'm trying to use a curly brace expansion in a Bash script, but it's not working for me in Ubuntu. It works in other distributions, like Arch, Fedora and Debian, and **it works in Ubuntu as well, but only from the command line, not in a Bash script**. I've tried it on multiple Ubuntu (10.04) machines, so it's not specific to one configuration. Here's what I did:

```
mkdir a b
```Now this works:```
ls {a,b}
```But if I create a file foo.sh, and put```
ls {a,b}
```in it and run it, I get this:```
ls: cannot access {a,b}: No such file or directory
```It's not parsing the expansion. Any ideas?

---

### Post by DaithiF on 2010-07-20
Hi,
its because its not bash that is executing the script, it is dash.
do
```
ls -l /bin/sh

```
and you'll see that /bin/sh is a symlink to the dash shell.
To run the script under bash put in a #! /bin/bash shebang

---

### Post by valbaca on 2010-07-20
I'm not on my Ubuntu box right now but try:
```
ls "{a,b}
```
or
```
ls '{a,b}'
```
 
Make sure the first line of the bash script is
```
#!/bin/bash
```

---

### Post by CosineQuaNon on 2010-07-20
It was dash. This is a little bit of a problem, because I'm using curly brace expansions in an Autoconf script, and Autoconf doesn't let you force a specific shell (the user must do it manually when running configure).

---

