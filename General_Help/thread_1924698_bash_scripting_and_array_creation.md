---
title: "bash scripting and array creation"
date: 2012-02-13
forum: General Help
---

### Post by anirbanbhattacharjee on 2012-02-13
#! /bin/bash
my_arr=(1 2 3)

...This piece of code is throwing the following error
myArr.sh: 2: Syntax error: "(" unexpected

I am running ubuntu 11.10

---

### Post by surfer on 2012-02-13
works for me on ubuntu 11.10. just copy-pasted your program into a file... hmmmm....?

---

### Post by sisco311 on 2012-02-13
It's a Bash script, so you have to run it in bash, NOT in sh.

```
bash myArr.sh
```
or
```
chmod +x myArr.sh
./myArr.sh
```

---

