---
title: "Using awk to grab frist number series"
date: 2010-02-03
forum: General Help
---

### Post by buee on 2010-02-03
Hello, just wondering if this can be done as I'd like to use it in a script.

I want to take this:
```

root@ubox:~$ du /etc
80	/etc/laptop-mode/conf.d
4	/etc/laptop-mode/lm-ac-start
4	/etc/laptop-mode/lm-ac-stop
4	/etc/laptop-mode/nolm-ac-start
4	/etc/laptop-mode/batt-start
4	/etc/laptop-mode/nolm-ac-stop
124	/etc/laptop-mode
16	/etc/defoma/config
160	/etc/defoma/hints
204	/etc/defoma
8	/etc/firefox-3.5/pref
12	/etc/firefox-3.5/profile/chrome
48	/etc/firefox-3.5/profile
60	/etc/firefox-3.5
8	/etc/byobu
4	/etc/opt
68	/etc/speech-dispatcher/modules
12	/etc/speech-dispatcher/clients
96	/etc/speech-dispatcher
8	/etc/xulrunner-1.9.1
```

And just keep the file sizes at the very beginning, no spaces, no letters, nothing after the first series of numbers.  Then I want to output those to a file to be added together later.  I can handle the addition part, but awk confuses me :(

If it has any bearing, the endgame here is to create a script that will count files and file sizes, add them together on a daily basis to come up with a total.  We have a NAS for computer backups and I would like to be able to look at one line of text and see how much data and file count we've backed up from today.

---

### Post by gmargo on 2010-02-03
[FONT=monospace]This bit will strip all but the first column:
```
du /etc | awk '{print $1;}'
```[/FONT]And for good measure, this bit of awk will sum up a list of numbers from stdin:
```
awk '{ sum = sum + $1; } END { print sum; }'
```

---

### Post by paxxus on 2010-02-03
An all perl solution:

```
du /etc | perl -ne '/^(\d+)/; $s += $1; END { print "$s\n" }'

```

---

### Post by buee on 2010-02-03
> **gmargo said:**
> [FONT=monospace]This bit will strip all but the first column:
```
du /etc | awk '{print $1;}'
```[/FONT]And for good measure, this bit of awk will sum up a list of numbers from stdin:
```
awk '{ sum = sum + $1; } END { print sum; }'
```

Any way to strip the last line only?  It will vary so I can't use head or tail to my knowledge.

---

### Post by gmargo on 2010-02-03
> **buee said:**
> Any way to strip the last line only?  It will vary so I can't use head or tail to my knowledge.

Why can't you use head?  **head -n -1** pass everything except the last line.

---

### Post by t4thfavor on 2010-02-03
What kind of script do you use to backup? Could this not just be tgz'd then you could just figure out the size of the archive?

---

### Post by buee on 2010-02-03
> **t4thfavor said:**
> What kind of script do you use to backup? Could this not just be tgz'd then you could just figure out the size of the archive?

We do backups that range anywhere from 3GB up to 500GB so tarring would work with some backups but take forever on others.  It's just not economical.

> Why can't you use head? head -n -1 pass everything except the last line. 

I found this

```
du $LINE | awk '{print $1;}' > /opt/tmp1.txt
	sed '$d' /opt/tmp1.txt > /opt/tmp.txt
	rm -f /opt/tmp1.txt
```

Which I'm fine with since it modifies the actual file rather than just the output of the file.

I have another issue though.  Some file names have spaces in them.  What would be the correct way to find these spaces and preempt them with a \ so they can be interpreted, but without modifying the actual filename?

---

### Post by paxxus on 2010-02-04
Many years ago i also used awk/sed/grep etc to do text processing which often resulted in complicated scripts and pipes and temporary files and what not. Worse, the regular expression syntax vary among these tools.
 
Then I made a concious decision to only learn one tool, namely perl. It can do it all with simple one liners - and I only have to remember one tool syntax, which my pea brain likes :)
 
I do not understand your problem with the spaces in the file names, how is that relevant for creating the sum - are you talking about a new problem?
 
Anyway, the follollowing one-liner will take a list of file names (in this example generated from ls) and output a new list with \ in front of spaces.
 
```
 ls -1 | perl -pe 's, ,\\ ,g'
```
 
If you want to extract the file names from the du command you'd have to skip the leading number and spaces:
 
```
du /etc | perl -pe 's,^\d+\s*,,; s, ,\\ ,g'
```
 
Combining it all, generating the file list with \ in front of spaces and the sum as the last line:
 
```
du /etc | perl -pe 's,^(\d+)\s*,,; $s += $1; s, ,\\ ,g; END { print "$s\n" }'
```
 
Edit: It just occuered to me that the du command actually outputs the sum for the entire /etc directory as the last line. I probably don't understand what it is you want, but I had fun with perl on-liners at least :)

---

### Post by gmargo on 2010-02-04
> Some file names have spaces in them.  What would be the correct way to find these spaces and preempt them with a \ so they can be interpreted, but without modifying the actual filename?For a shell script, don't try.  Modify the "IFS" (Internal Field Separator) instead.

Here's a simple Bash script that demonstrates the principle.  It just runs "ls" and prints the names.  But you can run this and see that it handles names with spaces just fine.

```

#!/bin/bash
# Using bash to use arrays and arithmetic

# Put basenames of files in $NAMES[] array
declare -a NAMES
declare -i indx=0

# Allows file/directory names to contain spaces:
OIFS=$IFS
IFS='\

'
# Find all entries in this directory.
for FILE in `ls -A`
do
    NAMES[indx++]=$FILE
done

# Switch back to normal field separator
IFS=$OIFS

echo "There are ${#NAMES[@]} entries:"
for (( indx=0 ; indx < ${#NAMES[@]} ; indx++ ))
do
    FILE=${NAMES[indx]}
    if [ -d "$FILE" ]; then
        echo "\"$FILE\" is a Directory"
    elif [ -f "$FILE" ]; then
        echo "\"$FILE\" is a Regular File"
    else
        echo "\"$FILE\" is something else"
    fi
done


```

---

### Post by buee on 2010-02-04
Ok, so here's what I've got so far:

```

#!/bin/bash

#Need 3 stats
#Total number of backups
#Total number of files
#Total amount of data

#Files written:
#/opt/filecount.txt - Houses number of files total for stats file
#/opt/backups.txt - Houses number of backups total for stats file
#/opt/tmp.txt - Temporary storage of file sizes for counting files and totalling data
#/opt/datacount.txt - Houses number of bytes for stats file

#################################################################################
#	BACKUP COUNT AND FILE COUNT PORTION
#################################################################################

#Counting files
du /cust_backups | awk '{print $1;}' > /opt/tmp1.txt
sed '$d' /opt/tmp1.txt > /opt/tmp.txt
rm -f /opt/tmp1.txt
filecount="0"
while read LINE; do
	filecount=$(($filecount+1))
done < "/opt/tmp.txt"
echo "$filecount" > tmp1.txt
oldfc=$(cat /opt/filecount.txt)
newfc=$(($oldfc+$filecount))
echo "$newfc" > /opt/filecount.txt
cat /opt/filecount.txt

#Counting backups
backups=$(cat /opt/backups.txt)
y=$(find /cust_backups -maxdepth 1 -mtime -10 | wc -l)
y=$(($y-1))
z=$(($backups+$y))
echo "$y" > /opt/backups.txt
cat /opt/backups.txt


################################################################################
#	FILE SIZE PORTION
#################################################################################

#du /etc | awk '{print $1;}'
#awk '{ sum = sum + $1; } END { print sum; }'
b="0"
while read LINE; do
	a=$LINE
	c=$(($a+$b))
	b=$c
done < "/opt/tmp.txt"

tmp=$(cat /opt/datacount.txt)
bytes=$(($tmp+$c))
echo "$bytes" > /opt/datacount.txt
cat /opt/datacount.txt

echo "Since February 4th, we have done $z backups totaling $bytes bytes and $newfc files" > /home/nas/Desktop/stats.txt
rm -f /opt/tmp.txt

#Attempting to make the data size in to Gigabytes or Megabytes, not sure which yet
count=$((($c/1024)/1024))
echo "$count"

```

When I run it, I get this:

```

root@custbackup:/opt# ./Count_Size.sh 
208390          #Supposed to be file count
6               #Supposed to be number of main directories  
                #or backups
3270259000      #Total file size in bytes, I believe
3118            #Total file size in what I'm hoping to be GB

```

Now, when I run properties, it comes up with 772,741 files and 121.7GB which means the file size is almost triple what it should be and the file count is less than 1/3 what is should be.  What am I missing?

---

### Post by gmargo on 2010-02-04
It's because you're using **du** to count files, when you should be using **find**.  **du** is recursive and it summarizes info on a per-directory, not per-file, basis and it's cumulative, so your file count and disk usage statistics are way off.  

One other thing I would highly recommend.  Don't use hardcoded paths throughout your code. Put a block of variables at the top to define files and directories, and use the variables in the code. Something like this:
```

TOBACKUP=/cust_backups
FDIR=/opt

TEMP=$FDIR/tmp.txt
TEMP1=$FDIR/tmp1.txt
FILECOUNT=$FDIR/filecount.txt
BACKUPS=$FDIR/backups.txt
DATACOUNT=$FDIR/datacount.txt
STATSFILE=/home/nas/Desktop/stats.txt

```

---

### Post by buee on 2010-02-04
> **gmargo said:**
> It's because you're using **du** to count files, when you should be using **find**.  **du** is recursive and it summarizes info on a per-directory, not per-file, basis and it's cumulative, so your file count and disk usage statistics are way off.  

One other thing I would highly recommend.  Don't use hardcoded paths throughout your code. Put a block of variables at the top to define files and directories, and use the variables in the code. Something like this:
```

TOBACKUP=/cust_backups
FDIR=/opt

TEMP=$FDIR/tmp.txt
TEMP1=$FDIR/tmp1.txt
FILECOUNT=$FDIR/filecount.txt
BACKUPS=$FDIR/backups.txt
DATACOUNT=$FDIR/datacount.txt
STATSFILE=/home/nas/Desktop/stats.txt

```

Focusing on one issue at a time, I want to tackle the file count.  

```
root@custbackup:/opt# find /cust_backups -mtime -11 | wc -l
9469

```

That's way off.  I went through the man page but can't find a better option to find these files with better...or any accuracy.  What is your suggestion?

---

### Post by falconindy on 2010-02-04
A few things come to mind here:

* If you really need to count the lines in a file, use `wc -l < file`. It's important that you redirect the file and not simply supply it as an argument because the output will differ.

* When using find to count files, use the flags '-type f' to only count files. You can use wc -l again here: `find <dir> -type f | wc -l`.

* When using du, use the '-s' flag to summarize. You can get the size of a single directory (the true size) with `du -s <target_dir> | cut -d\  -f1`.

Don't be so hurried to go to programs like sed or awk in Bash scripts. More often than not, there's far simpler programs to accomplish what you want. Often, Bash can accomplish complex tasks on its own. There's some excellent resources on the web for learning more about Bash:

[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Happy hacking.

edit: You're getting improper results on the following...
```
while read LINE; do
	a=$LINE
	c=$(($a+$b))
	b=$c
done < "/opt/tmp.txt"
```
Because the variables are assigned inside the while loop. A while loop spawns a subshell which cannot modify its inherited (parent) environment. Put some echo statements for a, b, and c after the loop and you'll see that they're not the expected values.

---

### Post by gmargo on 2010-02-05
> **buee said:**
> Focusing on one issue at a time, I want to tackle the file count.  
```
root@custbackup:/opt# find /cust_backups -mtime -11 | wc -l
9469

```What is your suggestion?

To just find and count files modified recently
```

find /cust_backups -type f -mtime -11 | wc -l

```Or to get a little fancier, find (GNU find anyway) has a printf option, so we can gather multiple bits of info.
```

BYTESUSED=$FIDR/bytespace.txt      # sum of bytes in files
DISKUSED=$FDIR/diskspace.txt       # sum of 1024 disk blocks in files
FILELIST=$FDIR/filelist.txt        # List of files

find "$TOBACKUP" -type f -mtime -11 -printf "%k\t%s\t%p\n" > "$TEMP"
wc -l "$TEMP" > "$FILECOUNT"
cut -f 1 "$TEMP" | awk '{ sum = sum + $1; } END { print sum; }' > "$DISKUSED"
cut -f 2 "$TEMP" | awk '{ sum = sum + $1; } END { print sum; }' > "$BYTESUSED"
cut -f 3- "$TEMP" > "$FILELIST"

```

---

### Post by buee on 2010-02-05
> **gmargo said:**
> To just find and count files modified recently
```

find /cust_backups -type f -mtime -11 | wc -l

```Or to get a little fancier, find (GNU find anyway) has a printf option, so we can gather multiple bits of info.
```

BYTESUSED=$FIDR/bytespace.txt      # sum of bytes in files
DISKUSED=$FDIR/diskspace.txt       # sum of 1024 disk blocks in files
FILELIST=$FDIR/filelist.txt        # List of files

find "$TOBACKUP" -type f -mtime -11 -printf "%k\t%s\t%p\n" > "$TEMP"
wc -l "$TEMP" > "$FILECOUNT"
cut -f 1 "$TEMP" | awk '{ sum = sum + $1; } END { print sum; }' > "$DISKUSED"
cut -f 2 "$TEMP" | awk '{ sum = sum + $1; } END { print sum; }' > "$BYTESUSED"
cut -f 3- "$TEMP" > "$FILELIST"

```

I could not get this to work for me.  I did, however, get one working.  It's longer, and definitely not efficient, but it does work.  I have tested it non stop for an hour and it's working just fine.  I do have to clean it up a little bit, but here's the working draft.

```
start=$(cat /home/nas/Desktop/FileCount.txt)

find /cust_backups/* -maxdepth 0 -mtime -11 > /home/nas/Desktop/CheckingFiles.txt
echo "" > /home/nas/Desktop/tmp.txt

while read LINE; do
	find "$LINE" >> /home/nas/Desktop/tmp.txt
done < "/home/nas/Desktop/CheckingFiles.txt"
filecount=$(wc -l /home/nas/Desktop/tmp.txt | awk '{print $1;}')
cat /home/nas/Desktop/FileCount.txt
rm -f /home/nas/Desktop/CheckingFiles.txt /home/nas/Desktop/tmp.txt

end=$(($start+$filecount))
echo "$end" > /home/nas/Desktop/FileCount.txt
cat /home/nas/Desktop/FileCount.txt
```

I did take out the -type f because it was throwing off the numbers.  Properties included folders, so I just wanted to make sure I had as little margin of error as possible.

Now, I'm going to see if I can piece together a method for counting bytes that works for this system.

---

