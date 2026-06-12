---
title: "noob trying to learn bash.  Advice?"
date: 2012-09-10
forum: General Help
---

### Post by Predictability on 2012-09-10
I'm very new at bash scripting, and I'm making a bunch of scripts as practice.  This is a script I made that can count up or down at different intervals, but I'd like advice on how to improve it/learn more about bash scripting.  Can anyone recommend a good way to learn bash for noobs?  Here's my script btw:

```
#!/bin/bash

countdown=$3
original=$3
smh=1
clear
if [ $1 = '--help' ]; then
echo "**************************************************
Hello, and welcome to Predictability's Timer v1.0!
**************************************************
If you would like to count up, please say ./timer.sh -cu
If you would like to count down, please say ./timer.sh -cd

-s: Count up or down  from 1 by seconds.

-m: Count up or down  from 1 by minutes.

-h: Count up or down  from 1 by hours.

Here is an example of counting up by seconds:
./timer.sh -cu -s

And here is an example of counting down by seconds:
./timer.sh -cd -s 3"
fi

if [ $1 = '-cu' ]; then
   if [ $2 = '-s' ]; then
      while true; do
         sleep 1
         clear
         echo "$smh second(s) has passed"
         let smh=$smh+1
      done

         elif [ $2 = '-m' ]; then
            while true; do
               sleep 1m
               clear
               echo "$smh minute(s) has passed"
               let smh=$smh+1
            done

         elif [ $2 = '-h' ]; then
             while true; do
                sleep 1h
                clear
                echo "$smh hour(s) has passed"
                let smh=$smh+1
                done
   fi

elif [ $1 = '-cd' ]; then

   if [ $2 = '-s' ]; then
      while true; do
      echo "$countdown seconds remaining."
      let countdown=countdown-1
      sleep 1
         if [ $countdown -eq -1 ]; then
            echo "Finished counting down from $original seconds."
            break
         fi
      clear
   done

elif [ $2 = '-m' ]; then
   while true; do
      echo "$countdown seconds remaining."
      let countdown=countdown-1
      sleep 1m
         if [ $countdown -eq -1 ]; then
            echo "Finished counting down from $original minutes."
            break
         fi
      clear
   done

elif [ $2 = '-h' ]; then
while true; do
   echo "$countdown seconds remaining."
      let countdown=countdown-1
      sleep 1h
         if [ $countdown -eq -1 ]; then
            echo "Finished counting down from $original hours."
            break
         fi
      clear
   done

   fi
         
fi

exit 0

```

---

### Post by cortman on 2012-09-10
Didn't look real hard at your script; but I'd break it into functions and call each function with an if/then statement.
For resources on learning bash, see the link in my signature.

---

### Post by Vaphell on 2012-09-10
bash supports arithmetic inside (()), eg
```
if (( countdown > 0 )); then (( countdown-- )); done
```


interpretation of script parameters often is done with *shift* and *case*
shift 'eats' current $1, and moves $2 in its place, $3->$2, etc. and reduces the value of $# (number of params) by 1.
It makes it easier to process the parameters in an arbitrary order, eg *program -a A -b B c d* vs *program -b B -a A c d* because you don't care about the correct number of $X


```
#!/bin/bash

# run case block if number of params > 0
# when it reaches 0, no unprocessed params
while (( $# )) 
do
  case "$1" in
            # if -a, take next param and save in a for future use
    -a)     echo a; shift; a="$1";; 
            # if -b, take next param and save in b for future use  
    -b)     echo b; shift; b="$1";;   
    -h)     echo help;;
    --help) echo help;;
    *)      echo \*;;
  esac
  shift  # move to the next param
done
```

---

