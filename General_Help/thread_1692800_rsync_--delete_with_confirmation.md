---
title: "rsync --delete with confirmation?"
date: 2011-02-21
forum: General Help
---

### Post by EntropyReduction on 2011-02-21
I want to synchronize sets of files (e.g. from or to flash memory).  rsync is powerful, but --delete option is dangerous.  

Anyone know whether there's a way to do --delete interactively, i.e. get rsync or some near equivalent to ask (y/n, in a console window) before deleting?

---

### Post by quixote on 2011-02-23
```
man rsync
``` doesn't show an interactive delete option.  But what you can do is use a -n option, for a simulated run, and a -v option for verbose output, and then pipe that output to a file. eg```
rsync -avn source target 1>rsync-dryrun.txt 2>rsync-dryrun-errors.txt
```That way you could check whether it plans on deleting too much.

---

### Post by gmargo on 2011-02-23
I usually throw in a "--max-delete=20" (or some other reasonable value) to limit potential damage.

---

### Post by EntropyReduction on 2011-03-01
I'm working on this: work in progress....anyone more expert on bash scripting thn me (which would be just about everyone, comments/changes welcome
```

#!/bin/bash

function processFilesInFolders
{
#$1 is source $2 is destination 

#bit of sanity checking

ARGS=2 # Number of arguments expected.
E_BADARGS=85 # Exit value if incorrect args passed.

 if [ $# -ne $ARGS ]
 then
  echo "usage: rsync_wrap souc_folder destination_folder"
  return E_BADARGS
 fi 

 if [ -z "$2" ]  ||  [ -z "$1" ]
 then
  echo "empty or missing parameters"
  echo "usage: rsync_wrap souc_folder destination_folder"
  return E_BADARGS
 fi 

 if [! -d "$2"] ||   [ ! -d "$1" ]
 then
  echo "parameter not a folder"
  echo "usage: rsync_wrap souc_folder destination_folder"
  return E_BADARGS
 fi 

 destLen=`expr length $2  + 2`
# destLen=`expr $destLen+ 2`
#echo path len $pathLen

 dirlist=$(find $2 -type d)
 for aDirec in $dirlist ; 
 do

   aDirecExclBase=`expr  substr $aDirec $destLen 200`
   fileList=$(ls $aDirec)

   for aFile in $fileList ;
    do
      if [  -f "$aDirec/$aFile" ] # exclude folders
        then
        if [ ! -e "$1/$aDirecExclBase/$aFile" ] # is it not in source?
          then
          read -p "$aDirecExclBase/$aFile is in destination but not source. Delete in destination (y/n)?"
          [ "$REPLY" == "y" ] || rm  -i "$aDirecExclBase/$aFile"
        fi  # if [ ! -e "$1/$aDirecExclBase/$aFile" ]
#     echo $aDirecExclBase/$aFile
      fi # if [  -f "$aDirec/$aFile" ] # exclude folders
    done  # after for aFile in $fileList 
 
 done # after for aDirec in $dirlist 
}

```

---

### Post by aeiah on 2011-03-01
you should wrap your code in ```
 tags, or [PHP] tags maybe to make it more readable.

i like the idea of doing a dry run first. and then using that output in a rm -i command

how's this for a one liner:
[code]
rm -ri `rsync -anv --delete $source/ $destination/ | grep deleting | sed 's/deleting /$destination/\/g'`

```

---

### Post by EntropyReduction on 2011-03-01
> **aeiah said:**
> you should wrap your code in ```
 tags, or [PHP] tags maybe to make it more readable.



Sorry.  Newbie.  Learning.  Done.

> i like the idea of doing a dry run first. and then using that output in a rm -i command

how's this for a one liner:
[code]
rm -ri `rsync -anv --delete $source/ $destination/ | grep deleting | sed 's/deleting /$destination/\/g'`

```Neat. 

I'll be back to you once I've taught myself enough sed to understand it.

---

### Post by EntropyReduction on 2011-03-03
> 
i like the idea of doing a dry run first. and then using that output in a rm -i command

how's this for a one liner:
```

rm -ri `rsync -anv --delete $source/ $destination/ | grep deleting | sed 's/deleting /$destination/\/g'`

```Okay, fiddled with the sed replacement.  Need "" instead of '' to get the variable parsed,
and since it's possible file names have spaces, need (?) to quote them; leaving out the rm -i :

```

rsync --delete --dry-run  --recursive --verbose  $source/   $destination/ | grep deleting | sed "s:deleting :$destination/:g" |  sed "s/\(^.*\)$/\'\1\'/g" 

```Okay, that gets me output on stdout like 

'/home/alan/Documents/temp/dest/test (copy).txt'

and

```

 rm -i '/home/alan/Documents/temp/dest/test (copy).txt'

```works

But when I tuck rm -i in front of rsync etc:
 
```

  rm -i `rsync --delete --dry-run  --recursive --verbose  $source/   $destination/ | grep deleting |   sed "s:deleting :$destination/:g" | sed "s/\(^.*\)$/\'\1\'/g" `

```somehow rm is getting the file names broken at white space ( it can't find files

       /home/alan/Documents/temp/dest/test
       (copy).txt
)

I tried wrapping file names in double quotes, same result.

Any ideas what I'm doing wrong?

---

### Post by gmargo on 2011-03-03
Don't use backticks.  Use a pipeline into xargs.

```

.... | xargs -d '\n' rm -ri

```

---

### Post by EntropyReduction on 2011-03-03
> **gmargo said:**
> Don't use backticks.  Use a pipeline into xargs.

```

.... | xargs -d '\n' rm -ri

```

Doesn't work for me: 

(a) I need to not add my own quotes with sed:
```

.... | sed "s/\(^.*\)$/\'\1\'/g"  | ....

```because it looks like xargs adds its own quoting, and 

(b) Looks like all files are sent to rm without waiting for interactive response from user.

---

### Post by EntropyReduction on 2011-03-07
This works:

```

rsync --delete --dry-run  --recursive --verbose  $source/   $destination/ | \
     grep deleting | sed "s:deleting :$destination/:g" |  \
     sed "s/\(^.*\)$/\'\1\'/g"  |  \
     xargs -n 1 -p -r  rm -i 

```xargs -n 1: "Use  at  most  max-args  arguments per command line"
         - p: "Prompt the user about whether to run each command line and  read
                a  line from the terminal"
         -r "If the standard input does not contain any nonblanks, do not run
              the command.  Normally, the command is run once even if there is
              no input.  This option is a GNU extension."

Thanks for pointing me in the right direction.

---

### Post by CaptainMark on 2011-03-08
> **aeiah said:**
> you should wrap your code in ```
 tags, or [PHP] tags maybe to make it more readable.

i like the idea of doing a dry run first. and then using that output in a rm -i command

how's this for a one liner:
[code]
rm -ri `rsync -anv --delete $source/ $destination/ | grep deleting | sed 's/deleting /$destination/\/g'`

```
Sorry but whats the g at the end for???

might be a silly question, forgive me if it is

---

### Post by EntropyReduction on 2011-04-25
I got that slightly wrong.  This works:

```


# sed pass 1:  clean up rsync output
# sed pass 2:  quotes around each file name (n case they contain blanks)
# rm:             don't use -i, interactive bit down with xargs -p option (got that wrong above)
 #                   -r allows folders to be deleted as well as files; 

   rsync --delete --dry-run  --recursive --verbose   $source   $destination | \
      grep deleting | sed "s:deleting :$destination/:g" |  \
      sed "s/\(^.*\)$/\'\1\'/g"  |  \
      xargs --max-args=1 -p  --no-run-if-empty  rm -r 

```

---

### Post by CaptainMark on 2011-04-25
I started off with just a one liner but i keep adding to it, ive got this now, ```
#!/bin/bash
# homesync
# mark skinner
# created 08/03/2011
# last modified 18/04/2011

source="/home/mark"
destination="/media/passport/mark"
parent="/.."
yes="y"
no="n"

echo "Detecting passport"
pass=`find $destination/ -maxdepth 0 2>/dev/null |wc -l`
if [ $pass == 0 ]; then
    echo -e "Passport not mounted\nExiting" && sleep 4 && exit
fi
echo "Passport found"

echo -e "Updating new files\nPlease wait"
rsync -aE $source/ $destination/
echo "New files copied"

echo "Detecting files to delete"
num_files=`rsync -avn --delete $source/ $destination/ |grep deleting |grep -Fv /. |grep -v "^deleting \." |wc -l`
if [ $num_files == 0 ]; then
    echo -e "No files to delete"
else
    echo -e "\nPreparing list:"
    rsync -avn --delete $source/ $destination/ |grep deleting |grep -Fv /. | grep -v "^deleting \." |sed "s/deleting / - /"
    
    echo -en "\nDelete these files? (y/n): "
    read delete1
    if [ $delete1 == $yes ]; then
        echo "Please wait"
        echo -n "5 " && sleep 1
        echo -n "4 " && sleep 1
        echo -n "3 " && sleep 1
        echo -n "2 " && sleep 1
        echo "1" && sleep 1
        echo -en "\nAre you sure you want to delete? (y/n): "
        read delete2
        
        if  [ $delete2 == $yes ]; then
            rsync -a --delete $source/ $destination/ 
            echo -e $num_files "files deleted\nExiting" && sleep 4 && exit
        else 
            echo "No files deleted"
        fi
    else
        echo "No files deleted"
    fi
fi

echo -en "Would you like to run a restore operation? (y/n): "
read restore1
if [ $restore1 == $yes ]; then
    echo "Please wait"
    sleep 3
    echo -e "\nThe restore will not delete files at the source"
    echo -en "Are you sure you want to restore? (y/n): "
    read restore2
    if [ $restore2 == $yes ]; then
        rsync -a $destination/ $source/
        echo "Backup files restored to main drive"
    fi
fi

echo "Exiting" && sleep 4

```This is my first bash script that i actually use regularly, theres only one bit im not happy with but im still a beginner with bash so im proud of my script, i tried to write it to be as quick as possible

---

### Post by EntropyReduction on 2011-05-10
I *still* got it wrong.

```


# copy stuff
   rsync $RSYNC_EXTRA_ARGS  --verbose --human-readable --recursive --whole-file --times  --update --modify-window=2   "$source"   "$destination"

# now delete stuff, asking first

#rsync: $source is where files backed up from, $destination, where to
#          must be quoted in case folder names contains blanks
# sed pass 1:  clean up rsync output
# sed pass 2: quotes around each file name (n case they contain blanks)
#    rm:  don't use -i, interactive bit down with xargs -p option

   rsync --delete --dry-run  --recursive --verbose "$source"  "$destination" | \
      grep deleting | sed "s:deleting :$destination/:g" |  \
      sed "s/\(^.*\)$/\'\1\'/g"  |  \
      xargs --max-args=1 -p  --no-run-if-empty  rm -r  # -r allows folders to be deleted as well as files; 


```

---

