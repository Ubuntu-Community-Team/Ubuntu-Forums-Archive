---
title: "auto-delete script help"
date: 2009-08-17
forum: General Help
---

### Post by Darth_tater on 2009-08-17
i recently lost a copy of a script a friend wrote for me, so i attempted to write my own.  I need some experienced eyes to look this over and tell me if it will work and how i can add some other features.  I use CRON to run this every day; 

first, the code.

```
!/bin/bash
# auto deletes files older than 15 days in a specified directory.
# this keeps various public directories on my file server clean and disk usage low!
# this is so poorly written that you are free to use it (but i dont know why you would want to..!)


##### define my variables ####
#
### small things ###
Ver=".1"  #script version
Date='date'
#
### big things ####
DAYS=15 
# if not specified, we want to delete all files OLDER THAN 15 days
PATH=./  
#is this how i tell my script that i want it to run in the directory the user called it from?
numFiles='' 
#empty variable for now, this will be filled later
logfolder=/somerandomfolder/
#where i want to store log files


############ START OF SCRIPT ############

#initial logic#
echo "############ Auto Del ############"
echo "AutoDel cleanup script version $Ver has started running as of :"; date
echo "$USER started this madness!"
echo "########~Lets Get Started~########"

if [[ $1= *[^0-9]* ]]
	then
		echo "Deleting all files older than $DAYS days old";
	else
		$DAYS=$1
		echo "Custom date: files older than $DAYS days old will be deleted"
fi

if [ -f $2 ]
	then
		$PATH=$2
	else
		echo "path '$2' does not exist.  I will assume you meant $PATH"
fi

#action logic#

find $PATH -mtime +$DAYS -type f -print -maxdepth 1 -exec rm -f {} \; > #what should go here to allow a count and list of files deleted possible?


echo "########################################################"
echo "operations have finished"
echo "number of files deleted : $numFiles"
exit 0
```

features:

1)  I want to check to see if the first command line argument is an actual numerical value. I want a check to see if the second argument is a valid directory.  have i done this correctly?

2) I want the script to run EITHER with a specified directory (second command line argument) OR use the directory that the user called it from.  EXAMPLE:

[PHP]user@host:/home/some_user/$ myscript 20[/PHP]

will run in /home/some_user with a tolerance of 20 days instead of the default 15.

3) as specified in the script, i want to store the logs of this program in a set folder.  These logs should include the flowing:
[INDENT] 
a) the path the script was run in
b) the FILE NAME to be deleted (i dont want the full path)
c) the total number of files deleted
[/INDENT]


--- thanks for any and all help you scripting wizards can provide!  I am a (very) novice programmer that hopes to learn from your input!  i have done the best i can from reading various scripting guides and the like, i know the coding style is messy and needs work, but thats why i have come here!!!

thanks again!

---

