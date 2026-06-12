---
title: "bash - check varible lenth"
date: 2010-02-02
forum: General Help
---

### Post by bakegoodz on 2010-02-02
I want a line or lines to check for variable length in my script. I just want to check if a variable the user inputted is 4 characters long, and if it isn't to return a false or exit status of 0. Thanks!

---

### Post by geirha on 2010-02-02
```

# Bash
if ((${#var} == 4)); then
    echo good
else
    echo "$var is ${#var} characters long, must be 4"
    exit 1
fi

```

If you are scripting for POSIX sh (#!/bin/sh), you have to use the [-command instead of ((. 
```

# POSIX sh
if [ ${#var} -eq 4 ]; then ...

```

---

### Post by rnerwein on 2010-02-02
> **geirha said:**
> ```

# Bash
if ((${#var} == 4)); then
    echo good
else
    echo "$var is ${#var} characters long, must be 4"
    exit 1
fi

```If you are scripting for POSIX sh (#!/bin/sh), you have to use the [-command instead of ((. 
```

# POSIX sh
if [ ${#var} -eq 4 ]; then ...

```

hi
27 years unix expirance - but never stop learning - never seen before 
thaks :p
richi

---

### Post by bakegoodz on 2010-02-02
Thank you very much, I found the exit command can make the shell close. I used true and false instead


if ((${#part} == 4)); then
  true
  else
  false
fi

---

### Post by geirha on 2010-02-02
The if is a bit useless in your code-snippet there. You are doing the same as just doing: ```
((${#part} == 4))
```

---

### Post by bakegoodz on 2010-02-04
Even better :)
if ((${#part} != 4)); then
echo "Type in a partition you idiot"

---

### Post by geirha on 2010-02-05
Aha, you are checking if the user inputed a legal partition like sda1, sdb4 etc?

Note that a partition name may be longer that 4 characters; if you have a lot of partitions on one disk, it'll have to start using 2 digits at the end. Perhaps a better test would be to check if the inputed string is actually a valid partition? 

blkid will only return true if it is, so
```
if ! blkid "/dev/$part" >/dev/null; then
  echo "$part is not a valid partition." >&2
fi
```

The user running the script will need to have read access to the partitions though, which means it either has to be root or be a member of the disk group.

Another option could be to check if it starts with [sh]da[0-9] and is a block device in /dev.
```

if ! [[ $part = [sh]da[0-9]* && -b /dev/$part ]]; then
  echo "$part is not a valid partition." >&2
fi

```

---

