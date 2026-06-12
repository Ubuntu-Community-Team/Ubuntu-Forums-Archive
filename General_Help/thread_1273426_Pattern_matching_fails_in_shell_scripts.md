---
title: "Pattern matching fails in shell scripts"
date: 2009-09-23
forum: General Help
---

### Post by samaricsm on 2009-09-23
I have a pattern match that works fine at the command line, and if I source the shell script; i.e., *. ./script.sh*.  It fails on a syntax error, if I run the script as a normal script (*./script.sh*).  It also fails if I try to run it as root.  I have tried changing the first line to **#!/bin/bash**, but that has had no effect.  The offending line is 17.

Any ideas?

1  #! /bin/sh
2  # 
3  # Set the environment variables necessary for Java
4  
5  Java=/java6/jdk1.6.0_16
6  
7  # Include the Java SDK executables
8  PATH="${Java}/bin:${PATH}"
9  
10 # Set the variable for Tomcat
11 JAVA_HOME="${Java}"
12
13 #  Add the development directory to the CLASSPATH
14 devClass=/usr/home/samaricsm/java
15 if [ "${CLASSPATH}" = "" ]; then
16   CLASSPATH="${devClass}"
17 elif [[ "${CLASSPATH}" = +(*${devClass}*) ]] ; then
18     :
19  else
20     CLASSPATH="${CLASSPATH}:${devClass}"
21     fi
22 
23
24 export java
25 export PATH
26 export CLASSPATH

---

### Post by ibuclaw on 2009-09-23
> **samaricsm said:**
> I have a pattern match that works fine at the command line, and if I source the shell script; i.e., *. ./script.sh*.  It fails on a syntax error, if I run the script as a normal script (*./script.sh*).  It also fails if I try to run it as root.  I have tried changing the first line to **#!/bin/bash**, but that has had no effect.  The offending line is 17.

Any ideas?


My guess is that you must add support for extended glob matching in bash.

```
shopt -s extglob
```
Regards
Iain

---

### Post by NoaHall on 2009-09-23
What are you trying to do with [[ "${CLASSPATH}" = +(*${devClass}*]]? It needs a comparison there, not a set. And it would be +=, not = +

---

### Post by samaricsm on 2009-09-23
An excellect guess!   That did do the trick.  I will see what I can do to mark this thread solved.

---

