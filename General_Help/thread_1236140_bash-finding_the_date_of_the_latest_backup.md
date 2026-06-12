---
title: "bash-finding the date of the latest backup"
date: 2009-08-10
forum: General Help
---

### Post by motoperpetuo on 2009-08-10
i'm attempting to learn bash by going through the excellent "bash beginner's guide" at [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html). right now, i'm on the third exercise in chapter eight. it's a script that should perform backups, both full and incremental. i'm trying to write the incremental backup routine right now, and i'm stuck on getting the date the last backup was made. here's what i have so far:
```

#incremental backup
for loop01 in `ls -ltr $backupfolder/backup*`
do
loopoutput=$loop01
done
echo "latest backup is $loopoutput"

```
the -ltr options after ls should output a list of all my backup files in long format, organized in reverse order by date, so that the most recent backup is listed last. indeed, if i just type 'ls -ltr' at the shell in my backup folder, i get this output:
```

-rwxrwxrwx 1 sluggo sluggo   29 2009-08-02 22:01 backup_full.tar.gz.1249858088
-rwxrwxrwx 1 sluggo sluggo 1566 2009-08-09 16:48 backup_full.tar.gz

```
the loop in my script should (as far as i understand) cause the variable $loopoutput to contain only the last line of output when the loop finishes. if it were so, i could easily use an awk statement on this output to extract the date and time the latest backup was made.

unfortunately, my echo statement on the last line there tells me that:
```

latest backup is ./backups/backup_full.tar.gz

```
that is, the date information is not contained in the variable $loopoutput. is there any way to get the date output from 'ls -ltr' into this variable? is there an easier way to do what i'm trying to do (get the date the latest file with a filename starting with the word 'backup' was created)? maybe there is...i'm new at this.

---

### Post by motoperpetuo on 2009-08-12
i figured out a better way to do this, by using awk commands in my loop:
```

if [ $type01 = "incremental" ]
then
	#place location and name of latest backup in $lastbackup
	for i in `ls -ltr $backupfolder/backup* | awk '{print $8}'`
	do
	lastbackup=$i
	done
	echo "Latest backup is $lastbackup"

	#get date of $lastbackup
	lastbackupdate=`ls -l $lastbackup | awk '{print $6}'`
	echo "Latest backup was made $lastbackupdate."
fi

```
one of the things i'm picking up on over the last few days is that you should generally use awk to parse information from output and files. it's particularly useful for reading a text file line by line, for example.

---

### Post by DaithiF on 2009-08-13
Hi,
you could also avoid the loop entirely by using tail to just take the last line of output from ls -ltr

so, 
```
lastbackup=`ls -ltr $backupfolder | tail -1 | awk '{print $8}'`
```

i see you then run ls  again to grab the date of the file, thats fine, but just so you know, you could grab both filename and date into an array variable at the same time.  array variables are a little on the advanced side, and the syntax can be confusing, but if you're interested:
```
lastbackup=(`ls -ltr . | tail -1 | awk '{print $8, $6}'`)
```
lastbackup is now an array variable with 2 elements.  You can use them like this:
```
echo ${lastbackup[1]}
echo ${lastbackup[2]}

```

---

### Post by motoperpetuo on 2009-08-21
thank you, DaithiF. that's exactly the kind of advice i was looking for.

---

