---
title: "need help running a shell script"
date: 2009-09-10
forum: General Help
---

### Post by kobe81 on 2009-09-10
Hi folks, thanks for taking a look at this. I really appreciate it. I have a shell script written for csh and I need to run it on a Jaunty x86 machine and a Fedora 11 x86 machine. It launches a java program I need for a college homework assignment. Both of the machines have bash so far as I can tell, and I can't for the life of me find equivalent commands. Anyway here is the script. Thanks again.

#!/bin/csh
set JARDIR1 = "../jars"
set JARDIR2 = "./"
setenv CLASSPATH .:${JARDIR1}/PS.jar:${JARDIR1}/Jeli.jar:${JARDIR2}/PS.jar:${JARDIR2}/Jeli.jar
java -mx64m PS

---

### Post by DaithiF on 2009-09-10
try this:
```
#!/bin/bash
JARDIR1="../jars"
JARDIR2="./"
export CLASSPATH=.:${JARDIR1}/PS.jar:${JARDIR1}/Jeli.jar:${JARDIR2}/PS.jar:${JARDIR2}/Jeli.jar
java -mx64m PS
```

---

### Post by kobe81 on 2009-09-10
Thank you so much DaithiF. I changed **setenv CLASSPATH** to **export CLASSPATH=**, but I had no idea that I needed to change **set JARDIR1 = "../jars"** & **set JARDIR2 = "./"**.

---

