---
title: "bash script error &quot;let: not found&quot;"
date: 2012-02-20
forum: General Help
---

### Post by grahams on 2012-02-20
I have a bash script that started to fail with "let: not found" and I'm stumped as to why. 

To troubleshoot I created a very simple script (test.sh) which also fails.

#!/bin/bash          
let a = 1

sh ./test.sh 
./test.sh: 2: let: not found

Permissions are wide open
ls -l test.sh 
-rwxrwxrwx 1 graham graham 32 2012-02-20 11:27 test.sh

I'm running the sh from bash
ps 
  PID TTY          TIME CMD
 3800 pts/1    00:00:00 bash
 4658 pts/1    00:00:00 ps

Let works from the bash prompt
#let
bash: let: expression expected

My paths look OK (I think)

echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/NX/bin

thanks in advance

---

### Post by Doug S on 2012-02-20
I believe that sh now links to dash and not bash. See the link in /bin to know for sure for your system.
 
for your execution line try changing this:```
sh ./test.sh
``` to this```
./test.sh
```as I suspect your sh prefix might be overiding setting inside your script (I don't know for sure).
 
Hope this helps.

---

### Post by matt_symes on 2012-02-20
Hi

```
#!/bin/bash 
let a=1
```

Try removing the spaces between a = 1.

Kind regards

---

### Post by grahams on 2012-02-20
> **Doug S said:**
> I believe that sh now links to dash and not bash. See the link in /bin to know for sure for your system.
 
for your execution line try changing this:```
sh ./test.sh
``` to this```
./test.sh
```as I suspect your sh prefix might be overiding setting inside your script (I don't know for sure).
 
Hope this helps.

It did indeed, many thanks.

---

### Post by grahams on 2012-02-20
> **matt_symes said:**
> Hi

```
#!/bin/bash 
let a=1
```

Try removing the spaces between a = 1.

Kind regards

Thanks, you're right I shouldn't have the spaces, but sh now using dash rather than bash was my issue.

---

