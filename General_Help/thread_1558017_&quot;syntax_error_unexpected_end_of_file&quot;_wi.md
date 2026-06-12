---
title: "&quot;syntax error: unexpected end of file&quot; with source"
date: 2010-08-21
forum: General Help
---

### Post by mhtrinh on 2010-08-21
Hi,

I have a file :
```

if [ $# -lt 1 ]; then
    pushd ~
else
    pushd "$@"
fi

```

I got error when source it :
```

$ source scripts/cd.src
bash: scripts/cd.src: line 6: syntax error: unexpected end of file

```

This work on a OpenSuse 11.2 !! Did the syntax of Bash on Ubuntu changed ???
I'm using : Ubuntu 10.04 LTS. bash version :  4.1.5(1)-release (i486-pc-linux-gnu)

---

### Post by ajgreeny on 2010-08-21
I seem to recall reading somewhere or other that an empty line in certain scripts can cause failure.  You obviously have an empty line 6, so I just wonder - -?

---

### Post by mhtrinh on 2010-08-21
No, I checked that already : no empty line, no "\n" after "fi". 
And even with empty line after "fi", it the same error.

---

