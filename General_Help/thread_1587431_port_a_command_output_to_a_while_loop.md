---
title: "port a command output to a while loop?"
date: 2010-10-03
forum: General Help
---

### Post by outleradam on 2010-10-03
How can I port standard out from ls or any other command into a while loop?

```
while read line
do
if [ $line = "foo" ]
    echo "bar $line"
done < `ls`
```but the redirection of ls does not work.  How do I import standardout to a while?

---

### Post by lloyd_b on 2010-10-03
Try this:```
ls |
while read LINE; do
    if [ "$LINE" == "foo" ]; then
        echo "bar $LINE"
    fi
done
```

The "ls |" takes the output from the 'ls' command, and pipes it into the while loop.

Lloyd B.

---

### Post by outleradam on 2010-10-03
Well, thank you, but it's not exporting the variables.  What would be the proper way to do this?  In this example,  $basename (inside the case statement) echos, but $stars(outside the case statement) does not have any data.

```
#! /bin/bash
/usr/local/bin/mythicalPythonBindings.py --filename='1952_20100929081200.mpg' --DBHostName='192.168.1.110' --DBName='mythconverg' --DBUserName='mythtv' --DBPassword='mythtv' --output=./ReturnFile.txt --display|
   while read line
     do 
     case "$line" in
         "basename = "* ) 
    echo $line
              basename=`echo "$line" |sed s/'basename = '//g`
                echo $basename
         ;;
         "stars = "* ) 
    echo $line
              stars=`echo "$line" |sed s/'basename = '//g`
         ;;

     esac
   done
echo $stars
```Basically, this file mythicalPythonBindings.py displays a list of information which needs to be turned into variables.

How do I get the variables out?

---

### Post by lloyd_b on 2010-10-04
Ouch - bash invokes a subshell whenever you pipe the output of a command to a while loop, so variables inside of that loop are normally local to that subshell.  Which means (as you've discovered) that variables created/set inside of the while loop that a command is being piped to are not normally accessible outside of that while loop.

There's a simple shell trick to get around this that should work in your case:```
#! /bin/bash
/usr/local/bin/mythicalPythonBindings.py --filename='1952_20100929081200.mpg' --DBHostName='192.168.1.110' --DBName='mythconverg' --DBUserName='mythtv' --DBPassword='mythtv' --output=./ReturnFile.txt --display | [COLOR="Red"]{[/COLOR]
   while read line
     do 
     case "$line" in
         "basename = "* ) 
              echo $line
              basename=`echo "$line" |sed s/'basename = '//g`
              echo $basename
         ;;
         "stars = "* ) 
          echo $line
          stars=`echo "$line" |sed s/'basename = '//g`
         ;;

     esac
   done
echo $stars[COLOR="Red"];}[/COLOR]
```In this case, the "{}" characters define the limits of the subshell, rather than it being defined by the "while" loop, so the variable "stars" will contain what you expect.

Lloyd B.

---

### Post by outleradam on 2010-10-04
^^That does nothing more then extend the same command.  But I found the answer on stackoverflow

```
#! /bin/bash
executePythonBindings() { /usr/local/bin/mythicalPythonBindings.py --filename='1952_20100929081200.mpg' --DBHostName='192.168.1.110' --DBName='mythconverg' --DBUserName='mythtv' --DBPassword='mythtv' --output=./ReturnFile.txt --display; }
while read line
 do 
 case "$line" in
         "basename = "* ) 
              basename=`echo "$line" |sed s/'basename = '//g` 
         ;;
 esac
 done < <(executePythonBindings)
echo $basename
```which produces:
```
xbmc@XBMC-live:~$ dbTest
1952_20100929081200.mpg

```

basically, redirecting the function instead of a command.

---

