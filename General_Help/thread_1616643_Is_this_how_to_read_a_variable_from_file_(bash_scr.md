---
title: "Is this how to read a variable from file (bash script)"
date: 2010-11-08
forum: General Help
---

### Post by tobytoby on 2010-11-08
I googled and tried to find an easy step by step-by-step guide on how to use a bash script read a variable from a file.

This is the way I did it (but it does not really work so something is wrong, but what?)
(testfil2 contains one line that reads:pidnumber=1578

#!/bin/bash

value="/home/user1/Desktop/testfil2"
echo $value
kill $pidnumber

---

### Post by luvshines on 2010-11-08
> **tobytoby said:**
> I googled and tried to find an easy step by step-by-step guide on how to use a bash script read a variable from a file.

This is the way I did it (but it does not really work so something is wrong, but what?)
(testfil2 contains one line that reads:pidnumber=1578

#!/bin/bash

value="/home/user1/Desktop/testfil2"
echo $value
kill $pidnumber

Simply source the file in the script and the variable is available there```

[ -f "/home/user1/Desktop/testfil2" ] && source "/home/user1/Desktop/testfil2" || echo "File /home/user1/Desktop/testfil2 not found"

# Use an invalid pid as default for display
pidnumber=${pidnumber:-'-1'}

# Check what value you have got
echo $pidnumber

```

---

### Post by SeijiSensei on 2010-11-08
I'd use:

```

#!/bin/bash
SOURCE=/home/user1/Desktop/testfil2

ID=$(awk -F'=' '{print $2}' < $SOURCE)
echo $ID

```

---

### Post by tobytoby on 2010-11-08
great it worked! Thanks and it looked very well written!

What is the first bracket doing? 
[ -f...etc]

and this?:

pidnumber=${pidnumber:-'-1'}

---

### Post by luvshines on 2010-11-08
> **tobytoby said:**
> great it worked! Thanks and it looked very well written!

What is the first bracket doing? 
[ -f...etc]

and this?:

pidnumber=${pidnumber:-'-1'}

**[ -f... ]** is checking for the existing of the regular file. It sources the file only when it is true else echo's error message

```
pidnumber=...
```

pidnumber variable is being assigned a default value of -1 incase pidnumber is not already defined in the sourced file

---

