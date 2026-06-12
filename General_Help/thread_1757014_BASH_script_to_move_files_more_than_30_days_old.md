---
title: "BASH script to move files more than 30 days old"
date: 2011-05-12
forum: General Help
---

### Post by OldManRiver on 2011-05-12
All,

I need to move files to a backup drive if they are over 30 days old.  All I could find, when looking for scripts, were ways to sort files by date and the solutions were all over the place and nothing seemed simple or good.

I've thought of building my own running "ls -al > filelist.txt" type of approach and then processing the file, but not sure that is best way.  An array would be much easier and eliminate the file, but never done an array in bash, so might need help if I go that way.

Open to suggestions on this.

Thanks!

OMR

---

### Post by papibe on 2011-05-13
You can use the 'find' command to get the list of files you need to move. For example:
```
$ find /path/to/files -mtime +30
```
More info on 'find':
```
$ man find
```
I hope it helps.

---

### Post by OldManRiver on 2011-05-15
papibe,

Your command suggestion is great, but I'm getting all the temp files, with the "~" also.  At this point not sure if I want to keep that information and execute "rm" against them, to clean up, or whether to eliminate them.  As I was looking through the manpage, which is exhaustive, I noticed -type but this does not seem to encompass what I need so was looking at the -iregex filter.

What are your thoughts on handling this part?

Thanks!

OMR

---

### Post by papibe on 2011-05-18
'find' can handle logical operators, so I think something like this may be useful to you:
```
$  find /path/to/files -mtime +30 -not -iname '~*'
```
That is: find old files that NOT start with a ~

Regards.

---

### Post by OldManRiver on 2011-05-19
papibe,

Great code but had to tweak like:
```
find /path/to/files -mtime +30 -not -iname '*~'
```
then worked perfect.

Thanks!

OMR

---

### Post by OldManRiver on 2011-05-21
All,

Here is my code so far:```
#! /bin/bash
# Declare the functions
# Func: delFile - Delete the temp files
function delFile() {
   rm "$1" -fR;
   [ $? -ne 0 ] && echo $0: Error deleting $1/. Aborting. > /dev/stderr $$ exit 3
   #echo "File $1 deleted!";
}

# Func: movFile - Move the files to Target Directory
function movFile() {
#    mv "$1" "$2"  # Test with cp cmd below.
    cp "$1"  "$2";
    [ $? -ne 0 ] && echo $0: Error moving \"$2\" from $1 to $3/. Aborting. > /dev/stderr $$ exit 2
}

# Func: getFile - get just the Filename
function getFile() {
   fullfile=$1;
   filename=$(basename $fullfile);
   extension=${filename##*.}
   filename=${filename%.*}
}

# Func: chkDir - Check for valid Directory (target)
function chkDir() {
   SOURCE=$1;
   [ -d "$SOURCE" ] || (echo $0: \"$SOURCE\" is not the name of a directory. > /dev/stderr; exit 1)
}

logfl="/home/trix_dir.log";

# Set up and run test values with local directories
txdir="/home/ndavis/myfiles/Scripts";
budir="/backups";

# Get directory list, of files over 30 days old, from source directory
# The natural coding flow is to do all in single command line, but it is
# necessary to put the filelist into a file so that multiple actions can
# be taken on each line as it is read back.

if [[ $logfil ]]
   then
   delFile "$logfil";
fi
find $txdir -mtime +30 | sort > $logfl;

# Read the directory log into array
a=0;
while read line;do a=$(($a+1));
   if [[ $line == *~* ]]
      then
         delFile "$line";
      else
         echo $a $line;
         fname=getFile $line;
         mvfil="$budir/$fname";
         movFile "$line" $mvfil;
   fi
done < $logfl;
exit 0

# Also record into the database for retrival

function addRecord() {
}
```
Running this with local dirs, has worked great.

Since this is going to be moving to remotely connected devices on a Windows Server, I'm at the point to start my testing on that SAMBA share name so will next be testing the "chkDir" function.

Then, since this effects other programs that have the filename with path in a MySQL DB, I need to build the Function (now place holder only) "addRecord".  I'm still looking for examples on how to write to MySQL from BASH.

Will keep you posted on the outcome.

If you have sources, suggestion, etc. Please contribute.

Thanks!

OMR

---

### Post by linuxinstalledfromhdd on 2011-05-21
that looks awesome.. nice work:D

---

### Post by OldManRiver on 2011-06-04
All,

Having mount issues, will be back on this, once those are addressed.

OMR

---

### Post by OldManRiver on 2011-06-21
All,

Would post my mount Qs here except the 2 boxes I'm trying to mount on are CentOS and OpenSUSE.  I am going to bring the DVD home and see if it mounts here on my U boxes.  I know the unit is working as we can put it in the OpenSUSE box and it auto mount on reboot there, but somehow can not get the manual mount string right.

Oh! have not been able to post on the CentOS forum, their sign-up/registration is not working right and will not give me access to POST on their forum.

At least if I could get this on the OpenSUSE box I could test.  Also could do either NFS or SAMBA share with the CentOS box (on same network) and get the job done in spite of CentOS and their forum problems.

Cheers!

OMR

---

### Post by idoitprone on 2011-06-21
the script you did looks complicated

```
find /path/to/files -mtime +30 -not -iname '~*' -exec rm '{}' \;

```


remove the files as it runs

---

### Post by OldManRiver on 2011-06-28
> **idoitprone said:**
> the script you did looks complicated

```
find /path/to/files -mtime +30 -not -iname '~*' -exec rm '{}' \;

```


remove the files as it runs

idoitprone,

I want to move the files not remove them.  Only the mv command is acceptable.

Thanks!

OMR

---

### Post by idoitprone on 2011-07-04
```
find /path/to/files -mtime +30 -not -iname '~*' -exec mv '{}' /whatever/path/you/feel/like/it/ \;
```
i was using the rm command as an example. find is used for script purposes too. You can run a command as you find the files

---

### Post by makeen on 2012-04-20
move files to a backup dir if they are over X days old
using the path information from the file to
build a path from the given dir root if necessary.

```

usage: script.sh dir days backup_dir

```

script.sh
```

#! /bin/bash
find $1 -mtime +$2 -not -iname '~*' -exec ./script_.sh {} $3 \;

```

script_.sh
```

#!/bin/bash
d=$2$(dirname "$1")
mkdir -p "$d"
mv "$1" "$d"

```

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #3 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

