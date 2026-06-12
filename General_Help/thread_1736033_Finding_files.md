---
title: "Finding files"
date: 2011-04-22
forum: General Help
---

### Post by alexalghisi on 2011-04-22
I've just managed to recover over 490.000 (JPG ONLY) files , with "photorec" , ok . The problem is that they are in 1.000 folders , and the photos I want to recover are between 1 MB -> 3 MB . Is there a way to search in all that folders for the files between this size in the Ubuntu  OS ?:confused:

---

### Post by dino99 on 2011-04-22
looks like a sql request script

---

### Post by alexalghisi on 2011-04-22
Nope , I managed to do it from the Terminal with "find" function , now the problem is , how can I delete all the empy folders with one comand ? There are over 100 empty folders :mad:

---

### Post by _nikolaos on 2011-04-22
This script is not actually finding files, but it can remove all empty directories into a filesystem tree, working recursively.

Please study it and experiment.

For example, if I create empty directories, one into another:
**mkdir empty1 empty1/empty11 empty1/empty12**
and use this
**rmemtptydir empty1**
then the script will remove everything empty, and report the process:
```
directory empty1 is not empty.
subdirectories are 2 : empty11 empty12
directory empty11 is empty and removed.
directory empty12 is empty and removed.
directory empty1 is empty and removed.
```

It will NOT remove directories that NOT empty (ie. they contain at least some file), it is very safe and I use it.

This is the script to copy:

```
#!/bin/bash
function dirempty()
{
    if [ $(ls -1A $1 | wc -l) -eq 0 ];
    then
        return 0
    else
        return 1
    fi
}

function removeempty()
{
    local test=$1
    if [ ! -w $test ]
    then
        echo "Permissions for $test denied."
        return
    fi

    if ( dirempty $test )
    then
        echo "directory $test is empty and removed."
        rmdir $test
    else
        echo "directory $test is not empty."
        cd $test
        local dirs=`ls -F1 | grep '/' | sed sx/xx`
        local count=`echo $dirs | wc -w`
        if [ $count -eq 0 ]
        then
            echo "No subdirectories in $test."
        else
            echo "subdirectories are" $count ":" $dirs
            local d
            for d in $dirs
            do
                removeempty $d
            done
            fi
        cd ..
        if ( dirempty $test )
        then
            removeempty $test
        else
            echo "There are some files and the directory $test will not be removed"
        fi
    fi
}

if [ $# -eq 0 ]
then
    echo "no parameters"
    exit -1
fi

if [ $# -gt 1 ]
then
    echo "over-numbered parameters"
    exit -1
fi

testdir=$1

if [ ! -e $testdir ]
then
    echo "parameter $testdir does not exist."
    exit -1
fi

if [ ! -d $testdir ]
then
    echo "parameter $testdir is not a directory."
    exit -1
fi

removeempty $testdir

exit 0

```

---

### Post by nothingspecial on 2011-04-22
```
find -type d -empty
```

There will be other empty folders you may not want to remove so you may want to expand the find command. 

Is there another criteria you can use such as the modification time or names?

when you've got it right put ```
-exec rm -r '{}' \;
``` at the end.

---

