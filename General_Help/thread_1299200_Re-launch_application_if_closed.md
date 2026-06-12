---
title: "Re-launch application if closed?"
date: 2009-10-23
forum: General Help
---

### Post by ntwrkguy on 2009-10-23
Hi all-

I am attempting to create my own version of a thin client in order to repurpose desktops that we have at my agency. I am very close to success, I was just wondering if anyone knows how to script something to prevent an application from closing? The idea is if VMWare View is closed/quit/user logged off their session (client closes itself out as a result), it will relaunch the program with my custom switches.

Any ideas on how to tackle this?

---

### Post by nerdopolis on 2009-10-23
I don't know how to make an unkillable program. But I'll give an automatic recreate script a whirl.  I'll use compiz as an example.

```

#!  /bin/bash

#the program  being called is compiz. you can replace it with any thing you like, 
#with any arguments but the ampersand symbol must stay, and it needs at least
#one space character distance from the command line. It tells bash to run the 
#command, but run the rest of the script after it does so, instead of waiting for
#it to end

compiz --replace &



#this captures the process id number of the previous command. using the process
#id number instead of the program name, makes sure the script doesn't get
#confused if there was a second instance called.

processid=$!

#the two lines below start the infinite loop. The infinite loop will cycle every 60 seconds

while [ 1 ]
do




#list all processes running with ps. grab the first column from ps only, as it contains the Process ID numbers,  and then search for the process id with grep and count the 
#number of times it sees it (it should be one) if its zero the process died. It should never be able to reach two or above. Save the number of time grep sees the process id 
#to a variable

isrunning=$(ps -A | awk '{print $1} |grep $processid -c) 


#the two lines begin the if statement that will run the command below if the process dies
if [[ $isrunning -ne 1 ]]
then

#the program name. once again the ampersand is important. the example is compiz with debug enabled now. 
compiz --debug --replace &

#save the new command process id to a file
processid=$!

#end the if statement
fi

#pause the script for 60 seconds, so that it doesn't pelt the CPU constantly looking for the process.
sleep 60

#state the end of the loop. once it reaches this, everything between the beginning, and here gets run
done

```Unfortunately there still lies the problem that someone will try to kill the script. You could run it as root,  and do ```
su username -c command 
``` . that will actually work as even though you pick up the process id of su, su stays open with the process and dies when the process dies.  (unless if you have sudoers)


Unfortunately the problem will be how to get the username to su, and how to tell when they log off so you can stop the script.

Detecting logoff is easier.
in the users ~/.bash_logout script file just have it create a file in a location that they have permessions to. 
```
touch /path/to/file
```

if the .bash_logout file doesn't exist, just create it and make it executable.  in the script above yuo can have it scan for the file, by adding the following in the loop of the script above. This will delete the file once it sees it, and will kill the script
```

if [ -f /path/to/file]
then
rm /path/to/file
exit 0
fi

```
which will say, if the file exists just run the command. (then if users figure out they can kill the script by creating a certain file location, then there is an issue.)




for staring the script on logon you can add to the users script to create a file containing their userneme in the logon script (~/.profile)

echo $LOGNAME > /path/to/login/file 

and then in a system init script, have it look for the file continuously, and when it finds it, set the contents into a variable (it will be the user name)  and delete it.
```

#! /bin/bash
while [ 1 ]
do
if [ -f /path/to/file]
then
       username=$(cat /path/to/file)
       su $username -c /path/to/where/you /stored/your/script
       rm /path/to/file
fi
done

```

init scripts are stored in /etc/init.d  and are called from /etc/rcX.d folder as simlinks. you'll want the fifth run level in Ubuntu. so put the symlink in /etc/rc5.d/ as S99scriptname

---

### Post by squaregoldfish on 2009-10-23
If you only run one instance of your program, you can run a polling program to check if the process is running, and if not, run it.

So, bash*, you can do something like:

```
while true
do
pid=`pgrep <process>`
if [ -z $pid ]
then
    run program &
fi
sleep 2
done
```* Not tested, so no guarantees this will work as is.

This will check to see if your program is running every 2 seconds, and if not, start it.

Steve.

---

### Post by diesch on 2009-10-23
Usually
 ```

#!/bin/sh 
while true; do
   my_program
 done

```
should do the job.


If you want to be able to easily stop to loop use this one

```

#!/bin/sh

FILE="/var/run/stop_my_program"

rm -f "$FILE"

while ! test -e "$FILE"; do
  my_program
done

```

If you want to break to loop just create a file named var/run/stop_my_program

---

### Post by ntwrkguy on 2009-10-26
Thanks for the replies everyone, I'll give it a shot and let you know how it goes!

---

