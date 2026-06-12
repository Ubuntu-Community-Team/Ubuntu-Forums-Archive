---
title: "wrote a script that displays last login times for all users"
date: 2010-05-24
forum: General Help
---

### Post by archknight on 2010-05-24
Hey, after a lot of work, I think I have successfully written a script that displays the last login times of all users on a system. It gets the list of users from the directories in the /home folder and then finds the latest entry from the 'last' command for their login times. This may be a useful script for admins out there

I am not at all sure this is the best way of doing this or that there aren't ways that this script fails. At the moment, there are no users on my test system who haven't logged in so I am not actually sure that feature works. I imagine it does though. Please feel free to copy/use and/or criticize/correct. I would love it if we can make this script better. Take a look:

```

#!/bin/bash

# listusers
#Displays last login time of all users.
#By: archknight
#24 May 2010

#Get list of users from /home directory.
usersCount=0
for i in `ls -a1 /home | grep -v ^'[.]\|[..]'$ | sed s/' '/'\\ '/g`
do 
    users[$usersCount]=$i
    times[$usersCount]=""
    usersCount=$(($usersCount + 1))
done

#Find the latest entry from the 'last' command and remember the time.
BAKIFS=$IFS
IFS=$(echo -en "\n\b")
timesCount=0
for j in `last -R`
do
    #Get the name which is in the first column.
    name=`echo $j | cut -d ' ' -f1`

    #Compare the name to all known users.
    for ((i = 0; i < usersCount; i++))
    do
        if [ "${users[$i]}" = $name ]
        then
            #If a time isn't already listed for this user, add it.
            if [ ! -n "${times[$i]}" ]
            then
                times[$i]=`echo $j | awk '{print $3 " " $4 " " $5 " " $6}'`
                timesCount=$(($timesCount + 1))
            fi
            break
        fi
    done

    #If we have found everyone, exit early so we don't have to go through the whole log.
    if [ $timesCount = $usersCount ]
    then
        break
    fi
done
IFS=$BACKIFS

#Concatenate results together into a string.
for ((i = 0; i < usersCount; i++))
do
    if [ -n "${times[$i]}" ]
    then
        result="$result"$'\n'"${users[$i]} ${times[$i]}"
    else
        result="$result"$'\n'"${users[$i]} never"
    fi
done

#Display results in nicely formatted columns.
echo $result | column -t

```

---

### Post by archknight on 2010-05-24
I added a -R to the 'last' command so that whether or not a hostname is resolved with the last login doesn't affect the output. I also tested that the script is accurately detecting when someone has never logged in, which it is.

---

### Post by archknight on 2010-05-25
Does anyone have any tips for improving this code? Perhaps it can be written so it runs faster? Or maybe there is a nicer way of doing something in the script. Please let me know what you think. Even a simple thumbs up or thumbs down is appreciated.

---

### Post by archknight on 2010-05-31
Nobody has any suggestions or comments?

---

