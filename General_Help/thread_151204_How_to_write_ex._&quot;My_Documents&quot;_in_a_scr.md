---
title: "How to write ex. &quot;My Documents&quot; in a script?"
date: 2006-03-27
forum: General Help
---

### Post by DrSkalpell on 2006-03-27
I have tried the following:

SOURCES="/media/windows/My Documents"
SOURCES="/media/windows/"My Documents""
SOURCES="/media/windows/My\ Documents"

Nothing works...

This is where I get the error message:

echo "Verifying Sources..."
for source in $SOURCES; do
	echo "Checking $source..."
	if [ ! -x $source ]; then
     echo "Error with $source!"
     echo "Directory either does not exist, or you do not have proper permissions."
     exit 2
   fi
done

Any suggestions? (I know - I have tested - that I have the proper persmissions)

---

### Post by 5-HT on 2006-03-27
What about trying one of these instead (quoting only the directory with single/double quotation marks, or just using an escape without quotations)?

```
 SOURCES=/media/windows/'My Documents' 
``` or ```
 SOURCES=/media/windows/"My Documents" 
``` or ```
 SOURCES=/media/windows/My\ Documents 
``` 
HTH

---

### Post by DrSkalpell on 2006-03-27
Thanks for helping, but that did not work either. I keep getting the same error message:

Ex. I type: SOURCES='/media/windows/"My Documents"'

Result:

Error with /media/windows/"My!
Directory either does not exist, or you do not have proper permissions.

---

### Post by lordofkhemenu on 2006-03-27
[quote=DrSkalpell]Thanks for helping, but that did not work either. I keep getting the same error message:

Ex. I type: SOURCES='/media/windows/"My Documents"'

Result:

Error with /media/windows/"My!
Directory either does not exist, or you do not have proper permissions.[/quote] "My Documents" is usually in a user folder, ie ```
C:\Documents and Settings\[username]\My Documents
``` 
So something like ```
/media/windows/documents\ and\ settings/[username]/My\ Documents
``` is what you probably need

---

### Post by DrSkalpell on 2006-03-27
This is the actual folder (in the first post I just made up some examples):

/media/windows/Documents and Settings/test

And it just won't work....

Obvisously it has something to do with the script:

if [ ! -x $source ]; then
echo "Error with $source!"
echo "Directory either does not exist, or you do not have proper permissions."

Could it be something with the -x?? I have no idea what the -x does...
btw it works if I don't have folders named in windows-style

---

### Post by jrib on 2006-03-27
the problem is probably the spaces in your directory name.  I don't know how to properly handle those, so you might want to google for "filename space bash"

[edit] changing ```
if [ ! -x $source ]; then
``` to ```
if [ ! -x "$source" ]; then
``` seems to work

[edit2] too slow apparently :)

---

### Post by nanotube on 2006-03-27
[QUOTE=DrSkalpell]This is the actual folder (in the first post I just made up some examples):

/media/windows/Documents and Settings/test

And it just won't work....

Obvisously it has something to do with the script:

if [ ! -x $source ]; then
echo "Error with $source!"
echo "Directory either does not exist, or you do not have proper permissions."

Could it be something with the -x?? I have no idea what the -x does...
btw it works if I don't have folders named in windows-style[/QUOTE]

you should quote $source. as follows:
```
if [ ! -x "$source" ]; then
```
it should work then. :)
and btw, if you want to find out what -x does, do a "man test". -x tests if file/dir exists.

---

### Post by DrSkalpell on 2006-03-27
I changed $source to "$source", and tried with different combinations, but that did not help either.

---

### Post by 5-HT on 2006-03-27
Hey again,

I'm not any good at bash scripting, but from a test I ran I think this may do it (got rid of the SOURCES variable as it seemed to be causing problems):

```

for source in /media/windows/Documents\ and\ settings/test/* ; do
echo "Checking $source..."
if [ ! -x "$source" ]; then
echo "Error with $source!"
echo "Directory either does not exist, or you do not have proper permissions."
fi
done 
``` 
for the directory, I was going by one of your posts, but substitute:
/media/windows/Documents\ and\ Settings/test/* with the directory you want.


BTW, the '-x' tests if the file exists and is executable, to find out if it exists you can use '-e'.

Here is a great bash guide:
[http://www.tldp.org/LDP/abs/html/]("http://www.tldp.org/LDP/abs/html/")

Hope this helps.

---

### Post by engla on 2006-03-27
And here is a good link with simple tips

[Writing robust bash scripts]("http://www.davidpashley.com/articles/writing-robust-shell-scripts.html")

---

### Post by DrSkalpell on 2006-03-27
This is the original script:

#!/bin/sh
# Author: Brice Burgess - [email]bhb@iceburg.net[/email]
# rbackup.sh -- secure backup to a remote machine using rsync.

# Directories to backup. Separate with a space. Exclude trailing slash!
SOURCES="/home/wendy /home/daisy /var/mail"

# IP or FQDN of Remote Machine
RMACHINE=192.168.0.2

# Remote username
RUSER=brice

# Location of passphraseless ssh keyfile
RKEY=/home/user/rsync-key

# Directory to backup to on the remote machine. This is where your backup(s) will be stored
# Exclude trailing slash!
RTARGET="/home/user/backups/my_machine"

# Your EXCLUDE_FILE tells rsync what NOT to backup. Leave it unchanged, missing or
# empty if you want to backup all files in your SOURCES. If performing a
# FULL SYSTEM BACKUP, ie. Your SOURCES is set to "/", you will need to make
# use of EXCLUDE_FILE. The file should contain directories and filenames, one per line.
# An example of a EXCLUDE_FILE would be:
# /proc/
# /tmp/
# /mnt/
# *.SOME_KIND_OF_FILE
EXCLUDE_FILE="/path/to/your/exclude_file.txt"

# Comment out the following line to disable verbose output
VERBOSE="-v"

#######################################
########DO_NOT_EDIT_BELOW_THIS_POINT#########
#######################################

if [ ! -f $RKEY ]; then
  echo "Couldn't find ssh keyfile!"
  echo "Exiting..."
  exit 2
fi

if ! ssh -i $RKEY $RUSER@$RMACHINE "test -x $RTARGET"; then
  echo "Target directory on remote machine doesn't exist or bad permissions."
  echo "Exiting..."
  exit 2
fi

echo "Verifying Sources..."
for source in $SOURCES; do
	echo "Checking $source..."
	if [ ! -x $source ]; then
     echo "Error with $source!"
     echo "Directory either does not exist, or you do not have proper permissions."
     exit 2
   fi
done

if [ -f $EXCLUDE_FILE ]; then
EXCLUDE="--exclude-from=$EXCLUDE_FILE"
fi

echo "Sources verified. Running rsync..."
for source in $SOURCES; do

  # Create directories in $RTARGET to mimick source directory hiearchy
  if ! ssh -i $RKEY $RUSER@$RMACHINE "test -d $RTARGET/$source"; then
    ssh -i $RKEY $RUSER@$RMACHINE "mkdir -p $RTARGET/$source"
  fi

  rsync $VERBOSE $EXCLUDE -a --delete -e "ssh -i $RKEY" $source/ $RUSER@$RMACHINE:$RTARGET/$source/

done

exit 0

Your solution with replacing SOURCES with the actual test-folder works :) I would however prefer to be able to fill in several folders under SOURCES. 

I have also read the simple tips about writing robust bash scripts, and I don't understand why the "$source" method does not work...

---

### Post by nanotube on 2006-03-27
hey
i think i found the solution to your problem. you have to use an actual array. as follows:

```
SOURCES[0]="/home/wendy/My Documents"
SOURCES[1]="/home/daisy"
SOURCES[2]="/var/mail"

for source in "${SOURCES[@]}"; do
        echo "Checking $source..."
done
```

that
properly treats each element of the array SOURCES as a directory, rather than splitting it up with spaces (as you will see from the output of this test code).

problem with using a simple space separated list as you were is that there is no way to differentiate between a space inside a path, and a space between. using arrays does it for you.

to see more details, "man bash" and search for string "arrays" :)

---

### Post by DrSkalpell on 2006-03-28
Excellent. Thanks!

Now the only problem is with the last rsync command in the script:

rsync $VERBOSE $EXCLUDE -a --delete -e "ssh -i $RKEY" $source/ $RUSER@$RMACHINE:$RTARGET/$source/

It still does not understand how to read the sources correctly.

---

### Post by nanotube on 2006-03-29
try putting quotes around $source, as follows:

rsync $VERBOSE $EXCLUDE -a --delete -e "ssh -i $RKEY" "$source"/ $RUSER@$RMACHINE:$RTARGET/"$source"/

i think that should work...

---

