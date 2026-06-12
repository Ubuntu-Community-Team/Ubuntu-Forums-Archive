---
title: "comparing dates in bash"
date: 2009-08-03
forum: General Help
---

### Post by motoperpetuo on 2009-08-03
i have a bash script in which i want to compare two dates to see if the first is more than a week older than the second. the dates are in yyyy-mm-dd format. for example:

2009-07-30
2009-08-03

i can imagine how to do this with a few awk commands, along with some if statements and basic arithmetic in case the second date falls on the first week of the month (as in this case). still, i'd hate to reinvent the wheel if there is functionality in bash that can already do this with one simple comparison operator or something like that. is there an easier way to do this than what i have planned?

---

### Post by bodhi.zazen on 2009-08-03
see man find =)

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

---

### Post by kaibob on 2009-08-03
> **bodhi.zazen said:**
> see man find =)

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

I don't have an answer to the OP's question, but I was curious how the find command could be used to compare dates in a bash shell script.

---

### Post by kjohri on 2009-08-04
You can convert date into seconds since epoch (1970-01-01 00:00:00 UTC) and then compare the resulting values (seconds). For example,

$ date --date="2009-07-30" +%s
1248892200
$ date --date="2009-08-03" +%s
1249237800

Then,

$ a=`date --date="2009-07-30" +%s`
$ b=`date --date="2009-08-03" +%s`
$ if [ $a -gt $b ]
> then 
> echo a
> else
> echo b
> fi
b

---

### Post by Blundey on 2009-08-04
Maybe this simple snippet of code will help you understand better:

#GET DATE VARIABLES
Today=`date +%Y%m%d`
TwoDaysAgo=`date -–date=’2 days ago’ +%Y%m%d`
ThreeDaysAgo=`date -–date=’3 days ago’ +%Y%m%d`
FourDaysAgo=`date -–date=’4 days ago’ +%Y%m%d`
FiveDaysAgo=`date -–date=’5 days ago’ +%Y%m%d`
SixDaysAgo=`date -–date=’6 days ago’ +%Y%m%d`
SevenDaysAgo=`date -–date=’7 days ago’ +%Y%m%d`

#SETUP PATHS TO OLD BACKUPS
SevenDaysAgoTar=/mnt/usbdrive/backups/$SevenDaysAgo
SixDaysAgoTar=/mnt/usbdrive/backups/$SixDaysAgo
FiveDaysAgoTar=/mnt/usbdrive/backups/$FiveDaysAgo
FourDaysAgoTar=/mnt/usbdrive/backups/$FourDaysAgo
ThreeDaysAgoTar=/mnt/usbdrive/backups/$ThreeDaysAgo
TwoDaysAgoTar=/mnt/usbdrive/backups/$TwoDaysAgo
TodayTar=/mnt/usbdrive/backups/$Today

#DELETE ANY OLD BACKUPS IF THEY EXIST
rm -rf $SevenDaysAgoTar
rm -rf $SixDaysAgoTar
rm -rf $FiveDaysAgoTar
rm -rf $FourDaysAgoTar

---

### Post by motoperpetuo on 2009-08-04
> **kaibob said:**
> I don't have an answer to the OP's question, but I was curious how the find command could be used to compare dates in a bash shell script.

i looked around a bit in the find man page, and there does indeed seem to be a way to do what i want to do (ultimately, i want to see if a backup is over a week old) with find. there's an -atime option that lets you search for files that were last accessed nx24 hours ago. there are a few other time-based options too.

the other suggestions were good too. i really appreciate all of your help. i'll try to remember to post my code when i finally get this routine to work.

---

### Post by motoperpetuo on 2009-08-05
i'm not quite getting it to work with find and the -atime option. i tried the -ctime option too, but so far no luck with that one either.

the find manpage states that -ctime is based on the last time the file's "status" was changed, whereas -atime is based on the last time the file was accessed. so, i've tried statements like this:

```

find . -name 'backup_full.tar.gz' -atime +7

```
or
```

find . -name 'backup_full.tar.gz' -ctime +7

```
but i get no hits, even though the date that displays when i run this
```

ls -al back*

```
is several months old. does anybody know what exactly the date in the output below refers to? is last time modified, last time accessed, date created, or something entirely different?
```

-rwx------+ 1 mjmontgo ???????? 30561 Feb  2  2008 backup_full.tar.gz

```

---

### Post by motoperpetuo on 2009-08-05
ok, i got the above find statements to work by modifying them to use the -mtime option. also, it looks like there's a -newerXY option that may work.

---

### Post by motoperpetuo on 2009-08-05
as promised, here's my final code. well, not final, but this is a test script i wrote that takes a file name in the present working directory as an argument, then tests it to see if it's over a week old. i'll incorporate this technique into my main project.
```

#!/bin/bash
#Test whether or not a given file was last modified over a week ago

#Test that one and only one argument was supplied
if [ ! "$#" -eq 1 ]
then
        echo "Please supply one and only one argument."
        exit 11
fi

#Test the argument equals name of an existing file in the pwd
if [ ! -f $1 ]
then
        echo "File $1 not found."
        exit 12
fi

#find file if it is over seven days old and place filename in $file01
#then let user know whether or not it is more than a week old
file01=`find . -name $1 -mtime +7`
if [ ! $file01 = "" ]
then
        echo "$1 is more than a week old."
        else
        echo "$1 is not more than a week old."
fi

```
the first routine just checks to make sure the user supplied one and only one argument. the second checks that the file exists in the current directory. the third is the one that actually tests whether the file is more than a week old.

any suggestions or improvements welcome...i'm new at this.

---

