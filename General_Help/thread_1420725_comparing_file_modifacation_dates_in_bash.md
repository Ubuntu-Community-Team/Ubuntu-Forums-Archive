---
title: "comparing file modifacation dates in bash"
date: 2010-03-03
forum: General Help
---

### Post by edpatterson on 2010-03-03
I am trying to write a shell script that compares the time stamps of 2 files and 'does something' if they are not the name then make them the same. I tried something like
```

if [ date -r file1 -ne date -r file2 ]; then
 ...
fi

```
Which blew up in a spectacular fashion. I have tried numerous variations all of which fail for one reason or another.

What is the proper way to perform this (simple) task. I am betting I am making it much harder that it really needs to be.

Thanks for any assistance,
Ed

---

### Post by diesch on 2010-03-03
```
if [ file1 -ot file2 -o file2 -ot file1 ]; then
 ...
fi
```

---

### Post by edpatterson on 2010-03-03
Thanks, I am skimming through the Bash Reference Manual trying to find the section that covers -o. I thought it would be in file but no.

This is what I came up with which is not a eloquent as yours for the testing of dates.

Do you know a quicker/cleaner way to sync time stamps for staff.sem and staff?

Of course in production it does not echo anything, just reloads Squids config files when one of them lists gets updated.

```

staffDate=`date -r staff +%Y%m%d%H%M`
semDate=`date -r staff.sem +%Y%m%d%H%M`
if [ "$staffDate" != "$semDate" ]; then
  echo "Dates are different, reload config files"
  touch -t $staffDate staff.sem
else
  echo "Date are the same, nothing to do"
fi

```

---

### Post by gmargo on 2010-03-03
> **edpatterson said:**
> Thanks, I am skimming through the Bash Reference Manual trying to find the section that covers -o. I thought it would be in file but no.


The -o means OR. See the **test(1)** man page. The bracket ("[") is actually a command named test.

---

### Post by diesch on 2010-03-03
> **edpatterson said:**
> Thanks, I am skimming through the Bash Reference Manual trying to find the section that covers -o. I thought it would be in file but no.


It just means a logical **or**, see the documentation nof the *test* command in the *SHELL BUILTIN COMMANDS* section.

```
[ file1 -ot file2 -o file2 -ot file1 ];
```
means
"*if file1 is older than file2 or file2 is older than file1*"


> **edpatterson said:**
> 
This is what I came up with which is not a eloquent as yours for the testing of dates.

Do you know a quicker/cleaner way to sync time stamps for staff.sem and staff?

Of course in production it does not echo anything, just reloads Squids config files when one of them lists gets updated.

```

staffDate=`date -r staff +%Y%m%d%H%M`
semDate=`date -r staff.sem +%Y%m%d%H%M`
if [ "$staffDate" != "$semDate" ]; then
  echo "Dates are different, reload config files"
  touch -t $staffDate staff.sem
else
  echo "Date are the same, nothing to do"
fi

```

```
touch -r staff staff.sem
``` sets the time stamp of *staff.sem* to the time stamp of *staff*

---

### Post by edpatterson on 2010-03-03
> **diesch said:**
> It just means a logical **or**, see the documentation nof the *test* command in the *SHELL BUILTIN COMMANDS* section.

```
[ file1 -ot file2 -o file2 -ot file1 ];
```
means
"*if file1 is older than file2 or file2 is older than file1*"




```
touch -r staff staff.sem
``` sets the time stamp of *staff.sem* to the time stamp of *staff*

Thanks for the assistance and the education!

Ed

---

### Post by geirha on 2010-03-03
For bash scripting you should use [[ and (( rather than [. You should only use the [-command for sh scripts. See [http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031) for more information. Btw the BashGuide at that wiki is great. [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

To get help for built-in commands and keywords, use «help»

```
help [[
```

That one will tell you that you want to also read the help for test, so do «help test» as well.

Do you really need the timestamps to be exactly the same? Usually it's enough to just check if file1 is older than file2.

---

### Post by diesch on 2010-03-03
> **geirha said:**
> For bash scripting you should use [[ and (( rather than [. 

In cases like this there's no advantage of *[[* over *[* so it's fine to keep things portable.

---

