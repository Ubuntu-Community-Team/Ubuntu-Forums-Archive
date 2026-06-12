---
title: "shell Script Not working"
date: 2009-11-03
forum: General Help
---

### Post by newboymak on 2009-11-03
hi every one, 
i installed ubuntu recently about a fortnight ago, its working fine, i am happy with its elegance. 
 
however i am a newbie when it comes to shell programming. 
i am well versed with C/C++ programming. 
 
could anyone please debug dis one, 
i hve posted the code along with the output that the script is currently giving. 
please help. 


#!bin/sh
SECS=5
INTERVAL=5
OS=$(uname)

case $OS in 
AIX|HP-UX|SunOS)
F1=2
F2=3
F3=4
F4=5
echo "\nthe operating system is ...$OS"
;;

Linux)
F1=3
F2=4
F3=5
F4=6
echo "\nthe operating system is ...$OS"
;;

*) echo "error:$OS is not a supportes os"
echo "\n\t...exiting..\n"
exit 1
;;
esac


echo "\ngathering cpu stats using sar ...\n"
echo "there are $INTERVAL sampling periods with\n"
echo "each inter lasting $SECS sec\n"
echo "...pls wait while gathering stats...\n"

sar $SECS $INTERVAL | grep Average \
| awk '{print $'$F1', $'$F2', $'$F3', $'$F4'}' \
| while read FIRST SECOND THIRD FOURTH

do
        case $OS in
        AIX|HP-UX|SunOS)
            echo "\n user part is ${FIRST}%"
            echo "\n system part is ${SECOND}%"
            echo "\n I/O wait  is ${THIRD}%"
            echo "\n Idle time is ${FOURTH}%"
            ;;

        LINUX)
            echo "\n user part is ${FIRST}%"
            echo "\n nice part is ${SECOND}%"
            echo "\n system part is ${THIRD}%"
            echo "\n Idle time is ${FOURTH}%"
            ;;
        esac 
done




here's the output for the above script:

neo@Matrix-Vicky:~/Desktop$ sh run2.sh

the operating system is ...Linux

gathering cpu stats using sar ...

there are 5 sampling periods with

each inter lasting 5 sec

...pls wait while gathering stats...

neo@Matrix-Vicky:~/Desktop$ 


i think there's some problem with the "while read" line 
plz help

---

### Post by newboymak on 2009-11-03
Wel EveryOne just viewed my problem, i ended up solving it myself :p 
anyway thanks.

here is the solution::

uname gives the output as "Linux"
but in my script in the case i had written "LINUX"

the while loop was working fine, on finding no matching case, it just had to exit.

---

