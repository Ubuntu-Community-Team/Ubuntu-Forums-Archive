---
title: "Bash script - porting from a  working Redhat"
date: 2011-07-19
forum: General Help
---

### Post by kraken47 on 2011-07-19
I have a RedHat shell script that works properly for years. Part of the script calls an external program and gets information from the output, redirecting it to an output file. This file in turn is used to populate variables which are then provided as argument to a program at the end of the script.  

I can't figure out how to get the RedHat script (see snippet below) to function in an Ubuntu bash script. The full script is unhappy with the function braces and declares there's a mismatch and ends prematurely, or if I remove them, the script goes on to the end but the output file T does not contain the information needed later.

What's required in my script to have the external program called and the output file be created? There is current data available in the external program, verified by manually running the commands between "END" markers. Issue must be in the script syntax. 

#!/bin/bash

case $# in
 1 ) DIR="."
     M=$1
     ;;
 2 ) DIR=$2
     M=$1
     ;;
 * ) echo "usage"
     exit 1 
     ;;
 esac

LOG=/tmp/im2png.log
mkdir -p $DIR >>/dev/null 2>&1
cd $DIR || exit 1

M=$1
T=$(mktemp -q /tmp/t.XXXXXX)
echo "about to enter im section " >  $LOG
{
im <<ENDS
.m1
$1
.s1

ENDS
} >$T 2>>/dev/null
echo "just passed by im section " >>  $LOG

HEAD=$(grep 'head:' $T | sed 's/^im> head: //')
W=$(grep 'width:' $T | sed 's/^width: //') 
H=$(grep 'height:' $T | sed 's/^height: //') 
TYPE=$(grep 'head:' $T | sed ' s/^im> head: //' | cut -c1-4)
cp $T /tmp/Tfile.txt

<<SNIP>>

---

### Post by AlphaLexman on 2011-07-19
I don't think you have given enough information.

I ran your snippet of code and got no errors.

What is your actual input and your expected output??

Post any errors you get.

---

### Post by mikejonesey on 2011-07-19
```
#!/bin/bash

function externalFunction()
{
    while read line; do
        echo $line
    done
}

function helloWorld()
{
    variablesToo=$1
    externalFunction<<EOF
i am a big brave dog!
$variablesToo
hope this was of some help...
EOF
}

helloWorld "wowsers..." > mylog.log 2>1&
```

ps you can write to dev null... (no need to append)

---

