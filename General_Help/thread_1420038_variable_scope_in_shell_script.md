---
title: "variable scope in shell script"
date: 2010-03-02
forum: General Help
---

### Post by blur xc on 2010-03-02
I sorry for asking so many scripting questions back to back- but I have another problem.

I'm trying to assign a value to a variable inside of an if statement that is inside of a while loop.  The variable doesn't seem to keep it's value outside of the while loop though.

Here's the code-
```
#!/bin/bash

FILEPATH=`date +%Y/%Y-%m-%d`
PROBLEM=""

if [ -d $FILEPATH ]; then
    echo "The directory already exists"
else
    mkdir -pv $FILEPATH
fi

#find /media/disk/DCIM -type f -exec cp -v '{}' $FILEPATH \;

find /media/disk/DCIM -type f | while read FILE; do
    NAME=`echo $FILE | cut -f5 -d"/"`
    if ! cmp -s "$FILE" "$FILEPATH/$NAME";then
        echo "There was a problem copying $NAME"
        PROBLEM="Yes"
        echo "inside if statement PROBLEM = $PROBLEM" 
    fi    
    echo "inside while loop PROBLEM = $PROBLEM" 
done
echo "outside while loop PROBLEM = $PROBLEM" 

if [ -z $PROBLEM ];then
    echo All files copied successfully!
fi
```I've got a bunch of extra echo statements in there to output the value for the variable PROBLEM every time it loops through the script.    Once I get past the "done" statement PROBLEM loses its value.  I thought if I initialized the variable at the top of the script it would make it global like in python, but it didn't work.  To force a failure I commented out the find command that copies the files, and intentionally modified one of the destination files.

Here's the terminal output from running the script:
```
 ./script.sh 
The directory already exists
inside while loop PROBLEM = 
inside while loop PROBLEM = 
inside while loop PROBLEM = 
inside while loop PROBLEM = 
inside while loop PROBLEM = 
inside while loop PROBLEM = 
inside while loop PROBLEM = 
inside while loop PROBLEM = 
There was a problem copying Filename with spaces.txt
inside if statement PROBLEM = Yes
inside while loop PROBLEM = Yes
inside while loop PROBLEM = Yes
inside while loop PROBLEM = Yes
inside while loop PROBLEM = Yes
inside while loop PROBLEM = Yes
outside while loop PROBLEM = 
All files copied successfully!
```Thanks,
BM

---

### Post by blur xc on 2010-03-02
I found out what my problem is- [http://www.kilala.nl/Sysadmin/index.php?id=741](http://www.kilala.nl/Sysadmin/index.php?id=741)

turns out bash spawns a sub shell when using pipes- and the variable scope isn't returned to the first shell...  hmmm....

BM

---

### Post by kaibob on 2010-03-02
The following FAQ further discusses this issue and suggests some workarounds.

[http://mywiki.wooledge.org/BashFAQ/024](http://mywiki.wooledge.org/BashFAQ/024)

For me, the easiest solution has been to "group the commands and do it all in the subshell." Utilizing DaithiF's example:

```
#!/bin/bash

find /home/kaibob/documents -type f | 
{
   while read file ; do
   echo "doing stuff with $file"
   PROBLEM="yes"
done

echo "all done, problem is $PROBLEM"
}
```

---

### Post by DaithiF on 2010-03-02
yes, so the solution is to avoid using a pipe.  there as various alternatives, redirect output to a file and then read from that file, or capture output in a variable, and read from that.

this one uses a temporary file to capture the find output and reads from that...
```
while read file
do
  echo "doing stuff with $file"
  PROBLEM="yes"
done < <(find /media/disk/DCIM -type f)
echo "all done, problem is $PROBLEM"
```

---

### Post by blur xc on 2010-03-02
> **DaithiF said:**
> yes, so the solution is to avoid using a pipe.  there as various alternatives, redirect output to a file and then read from that file, or capture output in a variable, and read from that.

this one uses a temporary file to capture the find output and reads from that...
```
while read file
do
  echo "doing stuff with $file"
  PROBLEM="yes"
done < <(find /media/disk/DCIM -type f)
echo "all done, problem is $PROBLEM"
```


Your implementation worked perfectly!  But- just a curiosity, is that a form of input redirection?  If so- why the double < < with the space in the middle?  

Thanks,
BM

---

### Post by geirha on 2010-03-02
<( ) is [process substitution](http://mywiki.wooledge.org/ProcessSubstitution).

Also see [http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001).

---

### Post by blur xc on 2010-03-02
thanks!

BM

---

