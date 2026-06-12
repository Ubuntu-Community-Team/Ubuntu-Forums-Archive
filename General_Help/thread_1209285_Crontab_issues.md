---
title: "Crontab issues"
date: 2009-07-10
forum: General Help
---

### Post by quesy on 2009-07-10
Hi guys, 

I'm having a very frustrating problem with crontab, ive tried to solve this problem now for two days, and still there is the same problem.

Enviroment for cron(*/2 * * * * /usr/bin/env >> /tmp/cepe.log):

SHELL=/bin/bash
XDG_SESSION_COOKIE=bee5fd2c6dc70015361db48d4a1170a1-1247213641.939302-1544481568
PATH=/etc:/bin:/sbin:/usr/bin:/usr/sbin
PWD=/home/johwal
SHLVL=1
HOME=/home/johwal
LOGNAME=johwal
_=/usr/bin/env

And the script is running:
*/2 * * * * /home/johwal/pz/projects/mailMover/mailMover.sh 2>&1 /tmp/cepe.log

The skript runs and everything, but it DON'T move any files as it should!

```

#!/bin/bash
_STRUCT="/home/johwal/pz/projects/mailMover/struct"
_LISTDIR="$_STRUCT/From"
 _WEEK=`date +%U`
_YEAR=`date +%Y`
_DATE=`date +%Y-%m-%d`

###Checking if DIR exsist#####

if [ ! -d $_STRUCT/$_YEAR ]; then
                 mkdir $_STRUCT/$_YEAR
#       echo "INBOX.$_YEAR" >> $_CURDB
fi

if [ ! -d $_STRUCT/$_YEAR.$_WEEK ]; then
        mkdir $_STRUCT/$_YEAR.$_WEEK
#       echo "INBOX.$_YEAR.$_WEEK" >> $_CURDB
fi

### Move files $_DATE

echo "Before for-loop .... " >> $_STRUCT/cepeskadad
for i in $(ls -l $_LISTDIR | awk '{print $6,$8}'| grep $_DATE | awk '{print $2}'); do
                    echo "nuff $i" >> $_STRUCT/cepeskadad
                    mv $_LISTDIR/$i $_STRUCT/$_YEAR.$_WEEK/
done
echo "After for-loop" >> $_STRUCT/cepeskadad

 
```OBS! This is my test-script, note the extra echo before and after for-loop.

The thing is that, the script make the dirs, echo Before for-loop and After for-loop, but inside the for-loop nothing happens, it dont echo nor move the files.

What the heck am i doing wrong ?? The script runs smooth interactive!

---

### Post by geirha on 2009-07-10
You just fell into bash pitfall number 1. Please fix that. [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Another way to get the date of a file is with date, GNU date that is (which is the one installed in Ubuntu). You can also use stat.

```
date --reference="$file" "+%Y-%m-%d"
```

The reason it doesn't work from cron though, is that you don't cd into the right directory. In an interactive shell, you'll start in your homedir, cron starts from /.

EDIT: No wait, assuming there's no paths with spaces, that's not it, I misread the script. The problem is probably the locale. cron doesn't use a locale, so it's ls output is different. Compare the output of "ls -l" in your current locale, and when locale is set to C: "LANG=C ls -l".

---

### Post by quesy on 2009-07-10
> **geirha said:**
> You just fell into bash pitfall number 1. Please fix that. [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Another way to get the date of a file is with date, GNU date that is (which is the one installed in Ubuntu). You can also use stat.

```
date --reference="$file" "+%Y-%m-%d"
```The reason it doesn't work from cron though, is that you don't cd into the right directory. In an interactive shell, you'll start in your homedir, cron starts from /.

EDIT: No wait, assuming there's no paths with spaces, that's not it, I misread the script. The problem is probably the locale. cron doesn't use a locale, so it's ls output is different. Compare the output of "ls -l" in your current locale, and when locale is set to C: "LANG=C ls -l".


How do i set the LOCALE in cron then ? Just LANG="C ls -l" in my crontab-file ?

---

### Post by geirha on 2009-07-10
C is the default locale, so if LANG is not set to anything else, LANG will C. You can see what your locale is set to by running the locale command with no arguments.

But really, do NOT parse the output of ls.

---

### Post by quesy on 2009-07-10
> **geirha said:**
> C is the default locale, so if LANG is not set to anything else, LANG will C. You can see what your locale is set to by running the locale command with no arguments.

But really, do NOT parse the output of ls.

Well i am not an uber scripter so thats why i use ls -l i don't find another way to do this, since its simple to get the file-name and date on the same line.

with stat i can't get the file-name easy, maby you know how to do this right ?

---

### Post by geirha on 2009-07-10
Try with something like:
```

for file in "$_LISTDIR/"*; do
    filedate=$(date --reference="$file" "+%Y-%m-%d")
    if [[ $filedate == $_DATE ]]; then
        echo "nuff ${file##*/}" >> "$_STRUCT/cepeskadad"
        mv "$file" "$_STRUCT/$_YEAR.$_WEEK/"
    fi
done

```

---

### Post by quesy on 2009-07-10
> **geirha said:**
> Try with something like:
```

for file in "$_LISTDIR/"*; do
    filedate=$(date --reference="$file" "+%Y-%m-%d")
    if [[ $filedate == $_DATE ]]; then
        echo "nuff ${file##*/}" >> "$_STRUCT/cepeskadad"
        mv "$file" "$_STRUCT/$_YEAR.$_WEEK/"
    fi
done

```


Tnx alot! Works like a charm!

---

### Post by quesy on 2009-07-10
Btw i diddnt fall in first pit =), i have space in dirs, but i wanted to be sure so thats why i took away the spaced dirs and "" =), but i did fall in that pit last night =)

Ty alot mate, so happy now =)

---

