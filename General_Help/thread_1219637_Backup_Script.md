---
title: "Backup Script"
date: 2009-07-22
forum: General Help
---

### Post by youknowhowiroll on 2009-07-22
Hey there,

I'm attempting to create a shell script using Ubuntu that will take one optional argument (which in this case is a path to a directory to backup) and will back up (by using the tar command) the chosen directory which is the /home. And i want, after tar'ing the home directory, for it to  save the output in /var/backups with the file name as the date. 

I'm very new to this so I was just hoping I could get pointed in the right direction!

Cheers.

---

### Post by LepeKaname on 2009-07-22
Save this code to (for example) backup.sh
```
#!/bin/sh

NOWTIME=$(date +"%b-%d-%y")
BAKFILE="$1-$NOWTIME.tar.gz"
STOREIN="/var/backups/"
BAKPATH=$1

tar cpvzf $STOREIN$BAKFILE $BAKPATH

```

Allow execution: 
```
chmod 755 backup.sh
```
You use it like: 
```
./backup.sh mydirectory
```

And will create: 

```
/var/backups/mydirectory-Jul-22-09.tar.gz
```

---

### Post by youknowhowiroll on 2009-07-22
Cheers for your help this has certainly sent me in the right direction!

---

### Post by youknowhowiroll on 2009-07-22
I also want to create it so that if an argument to the script is not supplied, it backs up the current users home directory. I also want the script to print an error message and exits the script if the directory could not be found. Any chance you could point me in the right direction for that?

---

### Post by LepeKaname on 2009-07-22
Sure, here you have:

```

#!/bin/sh

if [ $# -gt 1 ]; then
    echo
    echo "Usage: backup.sh [directory]"
    echo "If directory is not supplied, user's home directory will be used instead."
    echo
    exit 1
fi

NOWTIME=$(date +"%b-%d-%y")
BAKFILE="$1-$NOWTIME.tar.gz"
STOREIN="/var/backups/"

if [ $# = 0 ]; then # If no argument, use home directory.
    BAKPATH=$HOME
else
    BAKPATH=$1
fi

if [ -d $STOREIN ]; then # If backup dir exists...
    if [ -d $1 ]; then # If supplied dir exists...
        tar cpvzf $STOREIN$BAKFILE $BAKPATH
    else
        echo "Directory do not exists: $1"
    fi
else
    echo "Backup Directory do not exists: $STOREIN"
fi
echo "Done."

```

Explanation:

[ $# -gt 1 ] : means if 2 or more arguments were supplied.
[ -d $1 ] : if supplied directory exists

I didn't test it very much, but it should work. Be aware that if you want to backup a directory with spaces in it, you should quote it.

---

### Post by youknowhowiroll on 2009-07-22
Cheers for all your help mate...
One last newbie question lol i've been looking in the tar manuals and i was wondering if theres a way to hide tar errors..

e.g.

tar: Error exit delayed from previous errors

---

### Post by LepeKaname on 2009-07-23
In general I think it would not be a good Idea to hide those messages. That means you didn't have enough access permits to all the files within that folder (which in some cases may be important). 

I suggest to create a log file instead:

ADD:

```
...

STOREIN="/var/backups/"
[COLOR="SeaGreen"]BAKLOG="/tmp/backup.log"[/COLOR]

...
if [ -d $1 ]; then # If supplied dir exists...
    [COLOR="SeaGreen"]echo "$NOWTIME *******************" >> $BAKLOG[/COLOR]
    tar cpvzf $STOREIN$BAKFILE $BAKPATH [COLOR="SeaGreen"]>> $BAKLOG[/COLOR]
    [COLOR="SeaGreen"]echo "****************************" >> $BAKLOG[/COLOR]
else

...


```

The ">>" is to append to that log file. If you don't need the output, change the value of BAKLOG="/dev/null"

That's all... 

Don't be afraid of shell (bash) scripting, its kind of fun once you get into it. I will suggest you to read this site (its easy to understand):

[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

Good Luck!

---

