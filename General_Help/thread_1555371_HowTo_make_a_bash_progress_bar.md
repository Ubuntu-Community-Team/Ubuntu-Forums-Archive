---
title: "HowTo: make a bash progress bar"
date: 2010-08-18
forum: General Help
---

### Post by d3v1150m471c on 2010-08-18
Enjoy
```
#!/bin/bash
#########################################################
# Create and export a variable for our progress bar's
# percent.

export PERCENT="0"

##########################################################
# The following function is a usage example:
# We need to use a function with the progress bar
# because, you'll notice later in the code we
# need to have the "wait" command inside the function
# for this to work properly. If we have our wait function
# outside of our functions then the progress bar will
# not execute. Secondly, after setting the wait command
# in our function we'll have it create a test file that
# will tell our progress bar when to break its loop so
# we can update it and then move on to our next function.

EXAMPLE() {
sleep 3 & # <-- our command here must go into the background
wait # <-- wait will halt the following echo command until
     # the previous command in the background finishes :) .
echo "Stop Progress Bar" > ~/progress_test
}
##########################################################
# The following is our progress bar. We're going to use
# a creative if-then statement in a while-loop to pull this
# off. Looking at the code below we can visualize approximately
# what out progress bar will look like while it's executing.
# How this all works is like so:
# The progress bar will test to see if the "PERCENT" variable
# is less than 100. If it's less then it will continue running
# the progress bar until the status is 100 (or more). If it is more
# the break command will exit the while-loop after printing our %100
# status on the screen. The later half or our while-loop is important.
# If you remember the explanation above we created a progress_test file
# for our home directory. This part of our while-loop tests to see if
# the file exists and if so, breaks the loop. This has to be done
# appropriately in conjunction with the example function above; if
# not our progress_bar will run infinitely and our bash script will
# hang.

PROGRESS_BAR() {
while
if [ $PERCENT -lt 100 ]; then
     echo -ne "%$PERCENT  (<>        )"
     sleep .05
     echo -ne "\r\E[K"
     echo -n  "%$PERCENT  (  <>      )"
     sleep .05
     echo -ne "\r\E[K"
     echo -ne "%$PERCENT  (    <>    )"
     sleep .05
     echo -ne "\r\E[K"
     echo -ne "%$PERCENT  (      <>  )"
     sleep .05
     echo -ne "\r\E[K"
     echo -ne "%$PERCENT  (        <>)"
     sleep .05
     echo -ne "\r\E[K"
     echo -ne "%$PERCENT  (      <>  )"
     sleep .05
     echo -ne "\r\E[K"
     echo -n  "%$PERCENT  (    <>    )"
     sleep .05
     echo -ne "\r\E[K"
     echo -ne "%$PERCENT  (  <>      )"
     sleep .05
     echo -ne "\r\E[K"
     echo -ne "%$PERCENT  (<>        )"
     sleep .05
     echo -ne "\r\E[K"
  else
     echo -n "%$PERCENT  (<><><><><>)"
     echo -ne "\r\E[K"
     break
fi
do
if [ -e ~/progress_test ]; then
   rm -f ~/progress_test # <-- This is vital. If we don't
                         # delete this file it will kill
                         # our progress bar everytime
                         # we start it.
   break
else
   sleep .001
fi
done
}
#########################################################
# This last section is a usage example. It's pretty self
# explanatory: We set the "percent" variable to what we
# want our progress bar to tell us, next we run our function
# in the background so that our progress bar can execute,
# then we'll set the percent variable again to update the
# progress status for the next command. Repeat, repeat.
PERCENT="25"
EXAMPLE &
PROGRESS_BAR
PERCENT="50"
EXAMPLE &
PROGRESS_BAR
PERCENT="75"
EXAMPLE &
PROGRESS_BAR
PERCENT="100"
PROGRESS_BAR
#########################################################


```

---

### Post by earthpigg on 2010-08-18
usage example?

let's say im copying a 3gb file to a usb thumb drive. how would i use this script so that i can do it from a terminal and have a progress bar?

---

### Post by xenogia on 2010-08-18
> **earthpigg said:**
> usage example?

let's say im copying a 3gb file to a usb thumb drive. how would i use this script so that i can do it from a terminal and have a progress bar?


I too am interested in the script, but don't know how to really apply it.

---

### Post by Vaphell on 2010-08-18
i guess that in case of file copying you have to do ls -l on the destination file let's say every second. Destination file size will be different every time you do that, you need to get the number (with awk or whatever) and divide by the size of the source file to get the percentage which controls the state of the progressbar.

---

### Post by d3v1150m471c on 2010-08-18
You will need to modify the while-loop in the progress_bar function after creating some filesize variables. After that you will need some file tests to update the status.

Get the file size of the file to be copied:
```

FILE=`stat -c %s filename`

```Next, we'll need variables for our percent status. Since expr cannot use decimals we'll just multiply and set the percentage as if the file was larger.
```

P25=`expr $FILE '*' 25`
P50=`expr $FILE '*' 50`
P75=`expr $FILE '*' 75`
P100=`expr $FILE '*' 100`

```We'll need to add some variables to get the size of our new file then adjust it for the percent status.
```

NEWFILE=`stat -c %s newfile`
TESTSIZE=`expr $NEWFILE '*' 100`

```And finally we can throw these into the beginning of the while-loop:
```

[ $TESTSIZE -eq $P100 ] && PERCENT="100"
[ $TESTSIZE -ge $P75 ] && PERCENT="75"
[ $TESTSIZE -ge $P50 ] && PERCENT="50"
[ $TESTSIZE -le $P25 ] && PERCENT="25"

```

---

