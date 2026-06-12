---
title: "question on bash scripting"
date: 2011-03-22
forum: General Help
---

### Post by volvolinux on 2011-03-22
Hello 
 
I have a question on bash script.
 
what is the difference between:
 
MYUSER=`id -un $1`
 
 
and
 
 
MYUSER=`id -un `
 
 
the resutl is the same....

---

### Post by deconstrained on 2011-03-22
That's because $1 is an environment variable -- the first argument passed to the script at the command line. If you didn't pass it anything, it'll just be empty, so the two statements in backticks will be the same, more or less.

---

### Post by vivek.pandey on 2011-03-22
on terminal type this command
info coreutils 'id invocation'

you will get a manual page... read it

---

### Post by DaithiF on 2011-03-22
they will be the same only if the $1 variable expands to nothing, or to the currently logged in user.  $1 is a variable which contains the first parameter that was passed to the script when it was invoked (or nothing, if there was no such parameter).

so if your script was invoked like:
```
./yourscript bob
```
then 
```
id -un $1
```
would return bob
if your script was invoked without any parameters, ie.:
```
./yourscript

```then you will get the username of the currently logged in user.

---

### Post by volvolinux on 2011-03-22
ah, i see.
 
So that when I used the script in the secruity scirpt. i mean the script is in /etc/security , the $1 do make the sense.

---

