---
title: "bash script : mysql dump, crontab. help!"
date: 2010-03-03
forum: General Help
---

### Post by artheus on 2010-03-03
Hey!

I've made myself a little script, which I run in crontab.
The scripts purpose is to make a backup of the mysql-data stored in the computer.

Right now it just keeps filling up my computer with *.sql files.
What I would want to do is that the script checks how many backups is taken, and deletes folders with backup files, if it finds more than 5 folders. OK?

Here's my current script :

[PHP]#!/bin/bash

NOW=$(date +"%m-%d-%Y")
FULLNOW=$(date +"%m-%d-%Y %T")
HOUR=$(date +"%H-%M-%S")
SQLFILE="/backup/mysql/$NOW/sqldump-$HOUR.sql"

mnt_point=/backup
command=$(mount | grep $mnt_point | cut -d\  -f3)
#NOTE: in the above line there must be two spaces after cut -d\

if [ "$command" != "$mnt_point" ]; then
        echo "$FULLNOW  -  Error! No hdd mounted at /backup" >> /var/log/rsnapshot/mysql.log
else
        if [ ! -d "/backup/mysql" ]; then
                echo "$FULLNOW  -  Creating folder /backup/mysql" >> /var/log/rsnapshot/mysql.log
                mkdir "/backup/mysql"
        fi

        if [ ! -d "/backup/mysql/$NOW" ]; then
                echo "$FULLNOW  -  Creating folder /backup/mysql/$NOW" >> /var/log/rsnapshot/mysql.log
                mkdir "/backup/mysql/$NOW"
        fi

        if [ -d "/backup/mysql/$NOW" ]; then
                echo "$FULLNOW  -  Successfully made backup of mysql content." >> /var/log/rsnapshot/mysql.log
                mysqldump --create-options --all-databases --user="user" --password="password" --result-file=$SQLFILE
        else
                echo "$FULLNOW  -  Error making backup of mysql content." >> /var/log/rsnapshot/mysql.log
        fi
fi
exit 0
[/PHP]

Thanks!
//Artheus

---

### Post by gmargo on 2010-03-03
If you modify the name format of the $NOW backup directories to one that is more readily sortable (like YYYYMMDD), then it's easy to take advantage of some command line tools.

You are using (date +"%m-%d-%Y").
I suggest using (date +"%Y%m%d").

Then you can find all the directories more than 5 days old with a command like this:
```

ls 2* | sort -nr | tail --lines=+6

```

---

### Post by artheus on 2010-03-03
> **gmargo said:**
> If you modify the name format of the $NOW backup directories to one that is more readily sortable (like YYYYMMDD), then it's easy to take advantage of some command line tools.

You are using (date +"%m-%d-%Y").
I suggest using (date +"%Y%m%d").

Then you can find all the directories more than 5 days old with a command like this:
```

ls 2* | sort -nr | tail --lines=+6

```

Okay! Thanks! (Swedish date format....)

Will this make some kind of array? (I'm a little new beginner to bash..)
And how will I go on removing these folders?
With the rm -rf command, I guess. But how would it be done?

Thanks again!

---

### Post by gmargo on 2010-03-03
Backticks and capture the output
```

DIRS=`ls[COLOR=Black] /backup/mysql/[/COLOR] | sort -nr | tail --lines=+6`

for DIR in $DIRS
do
    if [ "x$DIR" != "x" -a -d "/backup/mysql/$DIR" ] ; then
        # remove echo when you're happy with this
        [COLOR=Red]echo[/COLOR] rm -rf "/backup/mysql/$DIR"
    fi
done

```

---

### Post by artheus on 2010-03-03
sorting seems to work with the current date format too..

```

artheus@www9:~$ ls /backup/mysql/ | sort -nr | tail --lines=+6
02-26-2010
02-25-2010
02-24-2010
02-23-2010
02-22-2010
02-21-2010
02-20-2010
02-19-2010
02-18-2010
02-17-2010
02-16-2010
02-15-2010
02-14-2010
artheus@www9:~$ ls /backup/mysql/ | sort -nr
03-03-2010
03-02-2010
03-01-2010
02-28-2010
02-27-2010
02-26-2010
02-25-2010
02-24-2010
02-23-2010
02-22-2010
02-21-2010
02-20-2010
02-19-2010
02-18-2010
02-17-2010
02-16-2010
02-15-2010
02-14-2010

```

Should I change the date format, or is it safe to trust that this will keep working?

Cheers

---

### Post by artheus on 2010-03-03
> **gmargo said:**
> Backticks and capture the output
```

DIRS=`ls[COLOR=Black] /backup/mysql/[/COLOR] | sort -nr | tail --lines=+6`

for DIR in $DIRS
do
    if [ "x$DIR" != "x" -a -d "/backup/mysql/$DIR" ] ; then
        # remove echo when you're happy with this
        [COLOR=Red]echo[/COLOR] rm -rf "/backup/mysql/$DIR"
    fi
done

```


I don't really understand the
```
if [ "x$DIR" != "x" -a -d "/backup/mysql/$DIR" ] ; then 
```
row. I mean the stuff like "-a", "-d" and similar. What do these mean?
I've seen these in other scripts too. Where can I read about them, and what are they called?

Thanks

---

### Post by gmargo on 2010-03-03
> **artheus said:**
> sorting seems to work with the current date format too..
Should I change the date format, or is it safe to trust that this will keep working?


Think about wrapping to the next year and you will know the answer.


> 
I don't really understand the
     Code:
     if [ "x$DIR" != "x" -a -d "/backup/mysql/$DIR" ] ; then 
row. I mean the stuff like "-a", "-d" and similar. What do these  mean?
I've seen these in other scripts too. Where can I read about them, and  what are they called?
See the **test(1)** man page.
In english, that if statement says "if $DIR is not the empty string AND if /backup/mysql/$DIR is a directory".

---

### Post by artheus on 2010-03-05
Thanks to you!

---

