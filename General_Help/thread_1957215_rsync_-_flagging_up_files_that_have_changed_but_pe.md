---
title: "rsync - flagging up files that have changed but perhaps should not have"
date: 2012-04-12
forum: General Help
---

### Post by moody_mark on 2012-04-12
Hi All,

I use rsync to backup files from one place to another. Its a great tool for backing up data from machines on your home network to a different machine. However heres my question:

Some files like pictures and music should never really change in size or modification data once they are backed up. By default I think rsync will backup only files that have changed. But lets say the source files get some kind of malware infection and change in size, I dont want rsync to back them up, instead I want to flag up an alarm or log it to a file.

Has anyone done this, is it possible with rsync?

Thanks!

---

### Post by papibe on 2012-04-12
Hi moody_mark.

rsync by itself won't help you take care of that concern.

However, it would be possible to create a bash script that will warn you, and thus stops running rsync.

The simplest method I can think of is using checksums. Let's say you have all the files that don't suppose to change in a directory called 'unchanged/'.

You could create the sums using something like this:
```
find unchanged/ -type f -exec md5sum '{}' \;  >  unchanged.md5
```
Then, every time you want to backup those files, you could check if they have change by using:
```
md5sum -c unchanged.md5
```
I hope that points you in the right direction. Tell us if you need more help with that.

Regards.

---

### Post by moody_mark on 2012-04-16
Thanks! I'll give this a try this week and post back

---

### Post by moody_mark on 2012-04-19
Hi, unfortunately this does not seem to work, heres a simple test I run using a directory with just one picture:

$ ls -l
total 8
-rw-r--r-- 1 user user 8028 2012-04-19 20:53 ZanesMessage.png


$ find . -type f -exec md5sum -c '{}' \; > unchanged.md5
md5sum: ./ZanesMessage.png: no properly formatted MD5 checksum lines found
md5sum: ./unchanged.md5: no properly formatted MD5 checksum lines found

---

### Post by papibe on 2012-04-19
Oops, my bad.

the -c option is for the second command (to actually 'check' the already created sums).

I corrected the commands now.

Regards.

---

### Post by moody_mark on 2012-05-05
Hi papibe, sorry late getting back to you, Ive finally got some time away from all the usual stuff to give this a try. It seems to work just fine, so thank you :-)

Now, I got to run this on a large directory of files which may also have new files in each time its run, so a couple more questions:

1. I would run the check (second command) first, which would check existing files and then I would run the generate command (first command) which would re-generate all the checksums correct?

2. Would it be more efficient to just generate checksums for new files and not generate the whole lot again (the first command seems to regenerate the whole lot)?

Thanks for your help, -Mark

---

### Post by papibe on 2012-05-05
> **moody_mark said:**
> 1. I would run the check (second command) first, which would check existing files and then I would run the generate command (first command) which would re-generate all the checksums correct?
As the previous given example, yes. And that would defeat the purpose of keeping then.

> **moody_mark said:**
> 2. Would it be more efficient to just generate checksums for new files and not generate the whole lot again (the first command seems to regenerate the whole lot)?
Not only more efficient, but necessary to avoid overwrite the previous sums.

The fact that you are adding new files, add a new variable that my previous example doesn't consider.

How about if you keep one md5 file for each file. Once an md5 file is created you never update it. You just create a new one only when a new content file appears in the unchanged/ directory

A couple of commands won't take care of this new logic, though. You would need to write a little bash script to implement it.

Tell us if you need help with the script.
Regards.

---

### Post by moody_mark on 2012-05-30
Hi, yes I think im going to need help getting this working... Heres what Ive tried so far:

1. Run the check on current files (this is ok, as we know from above)

md5sum -c <checkfile>

2. Now search our path for files and then find any new files (this seems problematic, it just my lack of cli knowledge). using simple "plain speak":

[LIST]
[*]find all files under <path>
[*]compare the files with the ones in <checkfile>
[*]the difference will be new files
[*]create new checksums for the new files
[/LIST]

Now the problem is using cat / grep etc I just cant seem to find the new files. For example:

```
find . -type f > filelist (finds all the files)
awk '{print $2}' checkfile (takes out the file name from the md5 check file)
```

but trying to grep out the difference doesnt work because you need to grep the right one and flag up the difference accordingly. I also tried diff but it means you got to create two files. I would have preferred to keep away from creating temporary files and just doing it in the command line, not that theres anything wrong with pushing things into temp files.

If you got any ideas then that would be great, thanks.

---

### Post by hjclaes on 2012-05-31
Hi moody_mark,

just another idea.

I don't know your other demands to your backup, but if you use storeBackup, you'll get all the md5 sums for free in each backup for each day.

There's a file called .md5CheckSums.bz2 with all md5 sums in each backup. You could filter the relevant files (eg. via grep and the path) and compare the results of two backups. (There is more information in it, but you can remove it with a simple sed command.)

Compared to rsync, you will also save a lot of space and it will administer deletion comfortable for you.

Look into chapter "special files generated and used by storeBackup". You can find storeBackup description at [http://lotte/storeBackup/en/]("http://lotte/storeBackup/en/la.html") It's delivered with ubuntu also, but unfortunately not in the actual version 3.2.1

Hope it helps

---

### Post by moody_mark on 2012-05-31
Hi hjclaes, I will look into that, thanks.

So I made a bit of a breakthrough and Im putting things into a script. In short this is the sequence of commands im going to use.


1. Make a list of files

```
find $CHECKDIRECTORY -type f > myCurrentList

```
2. Make a list of previous files

```
awk '{print $2}' myCheckFile > myOldList

```
3. Make a Comparision show only new files

```
grep -v -f myOldList myCurrentList > myNewList

```
4. Run md5sum of new items

```
cat myNewList | xargs md5sum >> myCheckFile

```
5. Check all md5sums

```
md5sum -c myCheckFile 

```
Note: the check file, temporary files will always fail
verification if they are in the same directory, but for my application the target directory will be different.

So my question is just how can you examine the exit status of the md5sum -c command in a script (i.e. no failures its ok? does that return a value i can examine?)

---

### Post by moody_mark on 2012-05-31
Ok I've kind of answered my own question, by setting the exit status of my script when the checksum fails. By checking the value of $? you can see if the script runs ok or not. I can of course trigger this from my server (which is the idea) and then if an error occurs send out an email and do not trigger the backup job

Here's the script in full. I'd appreciate any comments (its not quite finished, I need to add in capability for a switch to run in silent mode (from a cron job or server) or interactive mode from the cli:

```

#!/bin/bash
#*****************************
#checksum script for home system
#*****************************
#
#Version	Decription
#=======	============
#0.1		initial version

if [ -z "$1" ];then
	echo "Useage:" $0 "<directory path> (full paths are best)"
	echo "Example: "$0 " /home/user/Pictures"
	exit
fi

#Create variable for current date and log file name
TODAY=`date '+%Y%m%d_%H%M%S'`
LOGFILE=filecheck-$TODAY.log

#Setup flags and parameters
CHECKDIR=$1

#We make new md5sums for any new files
#add those to the checklist and then
#check all md5sums
#
#1. Make a list of files
#2. Make a list of previous files
#3. Make a Comparision show only new files
#4. Run md5sum of new items
#5. Check all md5sums
#
#Note: The checkfile and the other temp files
#will always fail md5sum verification after a
#the first couple of runs, this is because
#they change each time after the md5sum is
#generated for them. Because of this, we do not
#run this script against the same directory that
#the script is executed from
#
echo "*** starting check ***"
echo "*** starting check ***" > $LOGFILE
echo "generating lists of files from $CHECKDIR" >> $LOGFILE
#We have to echo the list and add quotes around the filename
#otherwise files paths with spaces are not escaped and cause
#problems
find $CHECKDIR -type f -exec echo "\"{}\"" \; > myCurrentList
awk '{print $2}' myCheckFile > myOldList
#the -x is used to match the whole line, not
#part of the line as some file names may be
#similar 
grep -vx -f myOldList myCurrentList > myNewList
#We must check if the file is empty otherwise
#xargs seems to generate a "-" which ends up in
#the checksum file and causes the script to hang 
#when it runs the md5sum -c command.
if [ -s myNewList ]; then
	echo "generating new checksums" >> $LOGFILE
	cat myNewList | xargs md5sum >> myCheckFile
else
	echo "no new files found, no new checksums to generate" >> $LOGFILE
fi
echo "verifying checksums" >> $LOGFILE
md5sum -c myCheckFile >> $LOGFILE
if [ $? = 0 ]; then
	echo "*** check successful ***" >> $LOGFILE
	echo "*** job complete, see $LOGFILE for any errors"
else
	echo "*** check unsuccessful ***" >> $LOGFILE
        echo "*** job complete, see $LOGFILE for any errors"
	exit 1
fi
#pause so the user can see the command window
#read -p "Press [Enter] key to quit..."

```

---

