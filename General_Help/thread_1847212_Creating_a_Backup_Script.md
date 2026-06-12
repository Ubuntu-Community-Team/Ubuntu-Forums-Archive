---
title: "Creating a Backup Script"
date: 2011-09-20
forum: General Help
---

### Post by scytherswings on 2011-09-20
Alright so this is my first backup script, I just got my crotabs to work backing up my server every 30 min, but I really don't need a new file every 30 min, so I am trying to have it back up only when the server is running. Here's my attempt so far.
Thanks much!
also the name of the script is serverchecker.sh

#!/bin/sh
######################################
# Check if Minecraft Server is running
# In order to prevent needless backups
######################################

RUNSTAT="$ps -C java -o pid=PID -o comm=CMD,args | grep -q Xincgc"

if [$RUNSTAT==0]; then
	echo "Starting Backup" && tar -vzcf /home/******/backup/minecraft.$(date +\%Y,\%m,\%d-\%H:\%M:\%S).tar.gz /home/******/Minecraft && echo "Backup Completed Successfully"
else
	echo "Server is Offline"
fi

---

### Post by scarleo on 2011-09-20
So this is not working or what exactly is your problem? Not sure I can help but if you want help you probably should be more specific to increase chance of someone helping you

---

### Post by aeiah on 2011-09-20
well... does it work?

how much do the server files change when its run? you're backing up everything each time and compressing them. it might be better just to back up the files that change and leave everything uncompressed. in this case, files that havent changed just point to previous versions and dont take up extra space. this sort of think is done using hard links, either with the cp -al command or rsync.

have a look here, it more or less explains it:
[http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

---

### Post by scytherswings on 2011-09-20
Thank's for the quick reply. The script does not work, the output i get is 


blah@blah:~$sh serverchecker.sh
test
[: 14: missing ]
Server is Offline



#!/bin/sh
######################################
# Check if Minecraft Server is running
# In order to prevent needless backups
######################################

RUNSTAT="$ps -C java -o pid=PID -o comm=CMD,args | grep -q Xincgc"
echo "test"

if [$RUNSTAT==0]; then
	echo "Starting Backup" && tar -vzcf /home/andrew/backup/minecraft.$(date +\%Y,\%m,\%d-\%H:\%M:\%S).tar.gz /home/andrew/Minecraft && echo "Backup Completed Successfully"
else
	echo "Server is Offline"
fi



As far as the files changing, not too much, probably 500kb to 3MB in a half hour, depending on activity of course. Backup space is not a problem as of right now, each compressed backup is about 25 -50MB atm.

Also I know that the 
ps -C java -o pid=PID -o comm=CMD,args | grep -q Xincgc 
command is supposed to exit with 0 if grep finds "Xincgc" which is why I am checking to see if it is  ==0. Not sure if that is working the way I'm intending though.
I'm thinking the syntax is a lot of my problem so far any pointers on that?
Thanks again.

---

### Post by aeiah on 2011-09-20
im not at a linux computer, so i cant tell what your syntax error is really. try and look at some examples i guess.


> **scytherswings said:**
> 
As far as the files changing, not too much, probably 500kb to 3MB in a half hour, depending on activity of course. Backup space is not a problem as of right now, each compressed backup is about 25 -50MB atm.


each backup may be 25-50mb (we'll say 38mb) but if that's every half an hour, you're chewing through a lot of space over days and days. in 24 hours your backups will be 1.8GB.

if you used snapshots, the space taken up would be the space of the first backup + the space of any changes, so that'd be just 72mb + the size of the first copy over a 24 hour period.

---

### Post by scarleo on 2011-09-20
I think you should take a look at rsync/d it probably does what you need, a lot easier than inventing the wheel all over again.

---

### Post by aeiah on 2011-09-20
ive just thought - instead of checking to see if the minecraft server  is running every half an hour via cron, why dont you just launch a script at the same time as the minecraft server? have it wait 30 minutes in an infinate loop?

```


<launch minecraft server> & while true; do <copy / rsync command>; sleep 30m; done
```

---

### Post by scytherswings on 2011-09-20
Ahh as much as rsync is useful, if I overwrite the previous files with the new ones, that defeats the purpose of this backup. Here are the reasons why: 
If a griefer decides to get on my server and destroy everything, rsync will overwrite the old "world" with the new, destroyed world.
Also if someone decides to create superusers etc...

This is bad. Thus my reason for needing a full backup. In theory I don't need a full backup every 30 min, like aeiah said that is hdd rape.. So if I can figure all this out, then the best thing would be to use a combination of both. Lets say an inc. backup every 30 min and a full every hour or so. However that still leaves the problem of making this script work. 
I did some more research and found that the "`" backquote character is used to execute commands, however I'm not sure if I'm using it right. Here's the current code. 

```

#!/bin/sh
######################################
# Check if Minecraft Server is running
# In order to prevent needless backups
######################################

RUNSTAT=`ps -C java -o pid=PID -o comm=CMD,args | grep -c Xincgc`;
echo $RUNSTAT;

if [$RUNSTAT == 1]; then
	`echo "Starting Backup"` && `tar -vzcf /home/******/backup/minecraft.$(date +\%Y,\%m,\%d-\%H:\%M:\%S).tar.gz /home/******/Minecraft)` && `echo "Backup Completed Successfully"`;
else
	echo "Server is Offline";
fi

```

and the output is:

blah@blah:~$: sh -x serverchecker.sh
+ ps -C java -o pid=PID -o comm=CMD,args
+ grep -c Xincgc
+ RUNSTAT=1
+ echo 1
1
+ [1 == 1]
serverchecker.sh: 1: [1: not found
+ echo Server is Offline
Server is Offline

---

### Post by scytherswings on 2011-09-20
> **aeiah said:**
> ive just thought - instead of checking to see if the minecraft server  is running every half an hour via cron, why dont you just launch a script at the same time as the minecraft server? have it wait 30 minutes in an infinate loop?

```


<launch minecraft server> & while true; do <copy / rsync command>; sleep 30m; done
```

Holy cow.. that's also not a bad idea, I could possibly run this type of command with two versions, one to do an inc. backup and the other command would do the full.. Nice!

So in that case, I should make a new launcher script that has these loops in it? I'm going to try and tackle this now.
Nice thing is that the server launch script is just minecraft.sh ...

---

### Post by scytherswings on 2011-09-20
Okay so I've tried to follow what you wrote. Here's the code:

```

#/bin/sh
#
#Launch minecraft server with backup loops
#
`sh minecraft.sh` & while true; 
	do 
`echo 'Starting Backup' && tar -vzcf /home/*****/backup/minecraft.$(date +\%Y,\%m,\%d-\%H:\%M:\%S).tar.gz /home/*****/Minecraft) && echo 'Backup Completed Successfully'`;
 sleep 1m; 
done

```
btw the sleep 1m is for testing purposes.

The output has some minecraft server output mixed in but I removed most of it for ease of debugging.

blah@Blah:~/Minecraft$ sh minecraftlaunch.sh
minecraft.sh: 2: -fn: not found
cd: 3: can't cd to ~/Minecraft
tar: Removing leading `/' from member names
12:28:35 [INFO] Starting minecraft server version Beta 1.8.1
...
12:28:37 [INFO] Done (0.169s)! For help, type "help" or "?"
tar: /home/******/Minecraft: file changed as we read it
minecraftlaunch.sh: 9: Starting: not found
...
tar: Removing leading `/' from member names
tar: /home/******/Minecraft/world: file changed as we read it
minecraftlaunch.sh: 9: Starting: not found
tar: Removing leading `/' from member names
minecraftlaunch.sh: 9: Starting: not found

... etc every minute tar outputs that of course.
Let me know what you think. Thanks

---

