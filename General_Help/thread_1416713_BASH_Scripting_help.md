---
title: "BASH Scripting help"
date: 2010-02-26
forum: General Help
---

### Post by #!akaGabe on 2010-02-26
I am currently writing a bash script for my work (a project that has to be written as a bash script) that will allow users to input there First 15 minute break, there lunch break and the last 15 minute break using zenity. I then have the script write this input into another file so that it will be stored on there box for the future. The issue i am running into is that i want the script to run in the back ground while they work and notify them at the time of there break (using zenity --warning) The difficulty I am having is that i dont know how to take the variable. My script right now lookes like this. 

```
 # Breaks input #

first15=""
lunch=""
last15=""
User=""

zenity --warning --title "Format" --text "please use military time, therefore 3:15pm=1515"

until [[ $first15 != "" ]]

    do

        first15=`zenity --entry --title "first 15 minute break" --text "please enter your first 15 minute break."`
       
if [[ $first15 == "" ]]

    then
        zenity --warning --title "Warning!" --text "You must enter your break time."
        
fi
 
if  [[ $? == "1" ]]
    
    then

    exit

fi
done

until [[ $lunch != "" ]]

    do

        lunch=`zenity --entry --title "Lunch Break" --text "please enter the time of your lunch break."`
       
if [[ $lunch == "" ]]

    then
        zenity --warning --title "Warning!" --text "You must enter your break time."
        
fi
        
if [[ $? == "1" ]]
    
    then

    exit

fi
done

until [[ $last15 != "" ]]

    do

        last15=`zenity --entry --title "last 15" --text "please enter the time of your last 15 minute break."`
       
if [[ $last15 == "" ]]

    then
        zenity --warning --title "Warning!" --text "You must enter your break time."
        
fi
        
if [[ $? == "1" ]]
    
    then

    exit

fi

done
sudo echo -e "$"First15:$first15"\n""$"Lunch:$lunch"\n""$"Last15:$last15 >> Break-Times.txt 

```The problem i am haveing is that what a person enters could be many differnt things so i thought of using this 

```

#!/bin/bash
ans=$(zenity  --list  --text "Please Select the time of your first 15 minute Break?" --radiolist  --column "Pick" --column "Break Time" TRUE "  1:00:00 AM" FALSE "  1:15:00 AM" FALSE "  1:30:00 AM" FALSE "  1:45:00 AM" FALSE "  2:00:00 AM" FALSE "  2:15:00 AM" FALSE "  2:30:00 AM" FALSE "  2:45:00 AM"  FALSE "  3:00:00 AM" FALSE "  3:15:00 AM" FALSE "  3:30:00 AM" FALSE "  3:45:00 AM" FALSE "  4:00:00 AM" FALSE "  4:15:00 AM" FALSE "  4:30:00 AM" FALSE "  4:45:00 AM" FALSE "  5:00:00 AM" FALSE "  5:15:00 AM" FALSE "  5:30:00 AM" FALSE "  5:45:00 AM" FALSE "  6:00:00 AM" FALSE "  6:15:00 AM" FALSE "  6:30:00 AM" FALSE "  6:45:00 AM" FALSE "  7:00:00 AM" FALSE "  7:15:00 AM" FALSE "  7:30:00 AM" FALSE "  7:45:00 AM" FALSE "  8:00:00 AM" FALSE "  8:15:00 AM" FALSE "  8:30:00 AM" FALSE "  8:45:00 AM" FALSE "  9:00:00 AM" FALSE "  9:15:00 AM" FALSE "  9:30:00 AM" FALSE "  9:45:00 AM" FALSE "10:00:00 AM" FALSE "10:15:00 AM" FALSE "10:30:00 AM" FALSE "10:45:00 AM" FALSE "11:00:00 AM" FALSE "11:15:00 AM" FALSE "11:30:00 AM" FALSE "11:45:00 AM" FALSE "12:00:00 PM" FALSE "12:15:00 PM" FALSE "12:30:00 PM" FALSE "12:45:00 PM" FALSE "  1:00:00 PM" FALSE "  1:15:00 AM" FALSE "  1:30:00 PM" FALSE "  1:45:00 PM" FALSE "  2:00:00 PM" FALSE "  2:15:00 AM" FALSE "  2:30:00 AM" FALSE "  2:45:00 PM"  FALSE "  3:00:00 PM" FALSE "  3:15:00 PM" FALSE "  3:30:00 PM" FALSE "  3:45:00 PM" FALSE "  4:00:00 PM" FALSE "  4:15:00 PM" FALSE "  4:30:00 PM" FALSE "  4:45:00 PM" FALSE "  5:00:00 PM" FALSE "  5:15:00 PM" FALSE "  5:30:00 PM" FALSE "  5:45:00 PM" FALSE "  6:00:00 PM" FALSE "  6:15:00 PM" FALSE "  6:30:00 PM" FALSE "  6:45:00 PM" FALSE "  7:00:00 PM" FALSE "  7:15:00 PM" FALSE "  7:30:00 PM" FALSE "  7:45:00 PM" FALSE "  8:00:00 PM" FALSE "  8:15:00 PM" FALSE "  8:30:00 PM" FALSE "  8:45:00 PM" FALSE "  9:00:00 PM" FALSE "  9:15:00 PM" FALSE "  9:30:00 PM" FALSE "  9:45:00 PM" FALSE "10:00:00 PM" FALSE "10:15:00 PM" FALSE "10:30:00 PM" FALSE "10:45:00 PM" FALSE "11:00:00 PM" FALSE "11:15:00 PM" FALSE "11:30:00 PM" FALSE "11:45:00 PM" FALSE "12:00:00 AM" FALSE "12:15:00 AM" FALSE "12:30:00 AM" FALSE "12:45:00 AM" );

echo $ans

```This would narrow the options used to a certian format of Hour:Minute:Second  "am/pm" so if the break was at 8:30 am it would look like 00:08:30 AM .  This seems to work fine as well but i dont know how to make it so the script will read this variable as a time stamp, recognize the time stamp and then announce at that exact time to go to the break.  I thought of something like...

```


if [[ $breaktime == date +%r ]]
    then
        zenity --warning --title "Break Time" --text "Enjoy your break see you in 15."
fi


```This doesn't seem to work with my logic.  I think that an until statement would work better like "until this is true then do nothing"  

Sorry im so noob with this but I cant seem to figure it out. Any and all advice will be greatly appriciated.  This script isn't set in stone so if you think that there is a more efficiant way or a easier way to get this to work please let me know.

Summery of my script.
* I want the user (employee) to be able to input there break times.
* I want the script to store the break times so that the user doesn't have to enter them everyday
* I want the user to be able to edit the times if necessary.
* I want the script to announce the time of the break.
* function correctly :S

---

### Post by Johnny B on 2010-02-26
you can use the date command to convert user input to whatever you want to work with, and nobody has to use military time. ex:

:~$ date +%I:%M%p --date="13:30"
01:30PM
:~$ date +%H:%M --date="1:30pm"
13:30


what is your job that you get to write bash scripts? i would love a job like that!

---

### Post by #!akaGabe on 2010-02-26
That will work great with the format. But how would i make the Bash script recognize the variable like $breaktime=10:45pm, execute at that time.

And i work for a tech support company that uses purely unix based os's

---

### Post by Johnny B on 2010-02-26
NOW=$(date +%I:%M%p)
if [[ $breaktime == $NOW ]] ;then
echo alarm
fi

---

### Post by #!akaGabe on 2010-02-26
i would like it to be an until statment because now executes right away. So how would i make it work with something like
```

until  [[ $breaktime == $NOW ]]

do nothing until [[ $breaktime == $NOW

```
or
```

if [[  $breaktime != $NOW ]]

then wait 

untill [[ $breaktime == $NOW ]]


```

sorry if this doesn't make sense. The codes provided are my though of how i would logically write it not necessarily syntax.  What i am trying to achieve is that the alarm will only sound once the time its supposed to. so i though that an until statment would do it but i dont know how to make an until statement just wait until the variable is correct... sorry again for being dumb

---

### Post by Johnny B on 2010-02-26
i never really liked until statements i would go with while, its really the same thing:

while true ;do 
NOW=$(date +%I:%M%p)
if [[ $breaktime == $NOW ]] ;then
echo alarm
break
fi
sleep 60
done

you can now reset the variable so it doesnt repeat
breaktime=

---

### Post by #!akaGabe on 2010-02-26
YES!!! IT WORKS!!!! omg ive been working on this all week.  You are a god send. I cannot believe how grateful I am!

If I can ask one more thing though. This is a project so i need to be able to explain what each part of the script is doing so could you maybe help me understand each line to to make sure i got it right?

while true ;do                               ##this is  going to wait until $breaktime == $NOW??
NOW=$(date +%I:%M%p)
if [[ $breaktime == $NOW ]] ;then ## i understand if/then
echo alarm                                   ## i understand echo
break                                           ## not sure what break command is
fi
sleep 60                                       ## not sure what this is doing...
done


You will be my hero lol :D

---

### Post by Johnny B on 2010-02-26
no problem, i got nothin to do today, too much snow :)

while true ;do ##this is going to loop forever (or until it encounters a break)
NOW=$(date +%I:%M%p)
if [[ $breaktime == $NOW ]] ;then ## i understand if/then
echo alarm ## i assumed you would replace this with a zenity command
break ## 'breaks' the loop, the next command executed is after 'done'
fi
sleep 60 ##  wait 60 seconds
done

---

