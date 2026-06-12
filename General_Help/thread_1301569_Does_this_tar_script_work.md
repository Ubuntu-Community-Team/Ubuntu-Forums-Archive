---
title: "Does this tar script work?"
date: 2009-10-26
forum: General Help
---

### Post by psycho5 on 2009-10-26
Hello dudes,

I am using crontab to schedule a backup script, and record everything to a file with the date. 

does this command accomplish this?

```

crontab -l
# m h  dom mon dow   command
0 2 * * 1-5 /home/oj/Documents/backup > /home/oj/Desktop/backup_$(date +%Y%m%d).log

oj@oj-desktop:~$ 
```

here's my backup script, its not for a server or such, just seeing if it will work..

```

#!/bin/bash

OUTPUT=/home/oj/Desktop/backup_$(date +%Y%m%d).tar.gz

BUDIR=/home/oj/Documents/

echo "Starting backup of $BUDIR to file $OUTPUT"

if [ `date +%w` -eq 4 ] ; then
tar -cvzpf $OUTPUT $BUDIR

fi

if [`date +%w` -gt 0 ] && [`date +%w` -lt 4] ; then

find $BUDIR -type f -newer $OUTPUT -print 0 | tar --null -czvf $OUTPUT -T-


if [ $? == 0 ]; then

mail -s "Backup successful for $OUTPUT" oj < ~

else
mail -s "Backup failed for $OUTPUT" oj < ~

fi 
fi

```

If anything's wrong here can someone please highlight it to me? Thank you!

EDIT: 

Something's wrong here, whats wrong with line 14?

```

./backup
Starting backup of /home/oj/Documents/ to file /home/oj/Desktop/backup_20091026.tar.gz
./backup: line 14: [1: command not found
oj@oj-desktop:~/Documents$ 

```

---

### Post by Giblet5 on 2009-10-26
Corrected in later post.

---

### Post by Giblet5 on 2009-10-26
PS: It is always a bad idea to assume that a file ($OUTPUT in this case) exists.

That's what 'test' (aka '[') is for.

You could probably precede line 14 with ```
test -f $OUTPUT && 
```
So, the working form could be ```
test -f $OUTPUT && find $BUDIR -type f -newer $OUTPUT | tar --null -czvf $OUTPUT -T-
```

---

### Post by psycho5 on 2009-10-26
Thanks, I wasn't aware of the "test" command. 

how about the crontab command, I can do > to_log_with_date.log ?

---

### Post by Giblet5 on 2009-10-26
> **psycho5 said:**
> Thanks, I wasn't aware of the "test" command. 

how about the crontab command, I can do > to_log_with_date.log ?

Maybe.

That depends on how cron decides to execute it, but yeah.

If the log thing is an inherent function of your script, then put it in the script: ```
#!/bin/bash

## Send all subsequent output to the log file:
LOGFILE="/home/oj/Desktop/backup_`date '+%Y%m%d'`.log"
exec > $LOGFILE 2>&1
...
```

---

### Post by psycho5 on 2009-10-27
Now I get this error: 

```

Starting backup of /home/oj/Documents/ to file /home/oj/Desktop/backup_20091027.tar.gz
tar: Removing leading `/' from member names
tar: /home/oj/Documents/backup\n: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors

```

If I hash out the first if statement along with the tar line and the second if statement, in other words, just let the differential backup run, I get the same error as above.

---

### Post by geirha on 2009-10-27
Sounds like you are missing -print0 at the end of the find-command.

---

### Post by psycho5 on 2009-10-27
Thank you, that worked I think, didn't return an error in the log file. Thanks alot! I think I'll mark it as solved now.

---

### Post by iMisspell on 2009-10-27
> **psycho5 said:**
> Now I get this error: 

```

Starting backup of /home/oj/Documents/ to file /home/oj/Desktop/backup_20091027.tar.gz
tar: Removing leading `/' from member names
tar: /home/oj/Documents/backup\n: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors

```

If I hash out the first if statement along with the tar line and the second if statement, in other words, just let the differential backup run, I get the same error as above.
Just ran into this problem while creating my first cron-job script...
For me it was a file path problem.


See if this works for you...
```


old_dir=`pwd`; # save current dir
cd /home/oj/ ; # change to parent dir of compress folder

if [ `date +%w` -eq 4 ] ; then
	tar -cvzpf /Documents $BUDIR # compress the 'Documents' dir
fi
cd $old_dir; # change back to orgenal dir


```

By going to the parent dir first, the compressed file will start with 'Documents' not '/home/oj/Documents/'
And also fix the "Removing leading `/' from member names" error.

[edit]
a slow typer i am :)
good to see you have it working.
_

---

### Post by geirha on 2009-10-27
Be careful with cd in scripts. If cd fails, you'll be issuing commands in the wrong directory. In this case, the tar will probably just fail, but what if it was rm for instance? 

Good practice is to always check the return value of cd. E.g.
```
cd /some/path || exit 1
```

On another note, [ is ancient, and if you are using bash, you might as well use bash's better features, like [[ and ((.
```

dow=$(date +%w)
if (( dow > 0 && dow <= 4 )); then ...; fi

```

---

### Post by iMisspell on 2009-10-28
> **geirha said:**
> Be careful with cd in scripts. If cd fails, you'll be issuing commands in the wrong directory. In this case, the tar will probably just fail, but what if it was rm for instance? 

Good practice is to always check the return value of cd. E.g.
```
cd /some/path || exit 1
```
Thanks for the insight, makes alot of sence.

_

---

