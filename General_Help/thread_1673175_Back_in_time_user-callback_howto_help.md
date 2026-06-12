---
title: "Back in time user-callback howto help"
date: 2011-01-22
forum: General Help
---

### Post by 987a654 on 2011-01-22
I am trying to understand these two examples for setting up user-callback option in back in time application. I am trying to modify this to suit my needs, google does not offer much help. Can someone help me with the syntax or at least point me to a resource that explains the syntax. I am not a programmer.

Back in time homepage has some basic info, but very terse, same with the man page. 

The following two examples are the only references I could find.

first one from here - [http://ubuntuforums.org/showthread.php?t=1334287](http://ubuntuforums.org/showthread.php?t=1334287)

I don't want email to be sent, just an update to the log file will be fine. 

#!/bin/sh
address ="<youruser>@gmail.com"
msg="To:<youruser>@gmail.com\n";
msg="${msg}Subject:Backup\n\n";
mailmsg=0;
case "$1" in
1);; ##Backup starting
2);; ##Backup finishing
3)msg="${msg} Backup completed for ${2} ${3}"
  mailmsg=1
 ;;
4)msg="${msg} An error occurred:"
  mailmsg=1
  case "$2" in
  1)msg="${msg} Application not configured";;
  2)msg="${msg} Process already running";;
  3)msg="${msg} Can't find directory";;
  4)msg="${msg} A snapshot for 'now' already exists";;
  esac
 ;;
esac
if [ $mailmsg = 1 ]
then
/bin/echo -e $msg | /usr/sbin/ssmtp $address
fi


Second Example is from here - [https://answers.launchpad.net/backintime/+question/133170](https://answers.launchpad.net/backintime/+question/133170)



!/bin/sh

report ()
{
    case $1 in
        #Application is not configured
        1) echo "Application is not configured" > /home/$user/backintime.log ;;
        #Take snapshot process is already running
        2) echo "Take snapshot process is already running" > /home/$user/backintime.log ;;
        #Can’t find snapshots directory
        3) echo "Can’t find snapshots directory" > /home/$user/backintime.log ;;
        #Snapshot for Now already exist
        4) echo "Snapshot for “now” already exist" > /home/$user/backintime.log ;;
    esac
}

proceed()
{
    case $1 in
        #Backup process begins.
        1) mkdir "/media/DriveName/"
           mount -t ext4 /dev/sdb1 "/media/DriveName/" ;;
        #Backup process ends
        2) sync
           umount "/media/DriveName/"
           rmdir "/media/DriveName/" ;;
        #There was an error
        4) report $2
           ;;
    esac
}

case $2 in
    #Profile Name
    BackupName)
                echo "Proceeding with BackupName" > /home/$user/backintime.log
                proceed $3 $4
                ;;
esac


I just need an explanation of the syntax, I want to understand it.

---

### Post by felichas on 2011-09-26
Hi 987a654,

You need some basic scripting knowledge to fulfill your requirement.
As you don't understand any of the scripts, I'll go ahead and try to explain script #1 as it is easier, and should be enough for what you need to do.
Keep in mind it has been created to work with a version of *backintime* < 1.0 (check [http://backintime.le-web.org/documentation/usercallback/]("http://backintime.le-web.org/documentation/usercallback/") )

Whenever *backintime* is run (check your crontab) 
it will look for a user callback script in ${XDG_CONFIG_HOME}/backintime/user.callback
this will most likely be ~/.config/backintime/user.callback

If this script is in the system, it will be called by Backintime at certain times during the backup process:
 [LIST]
[*]when Backup process begins, with '1' as the argument.
[*]when Backup process ends, with '2' argument.
[*]when A new snapshot was taken, with '3' as the 1st argument, the snapshot ID as the 2nd argument, and snapshot path as the 3rd.
[*]and whenever there is an error following the previous rule.
 [/LIST]

Therefore, when your backup begins, Backintime will call:
```
$ ~/.config/backintime/user.callback 1
```
and when a snapshot is taken, Backintime will call:
```
$ ~/.config/backintime/user.callback 3 20110926-124001 /snapshot/path
```

Now, if you want to do something special, you can catch those arguments and proceed acordingly.
This is what script #1 does, using the **case** command (check [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29]("http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Choices_.28case_and_select.29") )

 [LIST]
[*]First, the scripts defines itself as an sh script.
[*]it then defines 3 variables to be used later: address, msg, mailmsg.
[*]and using **case** checks the value of the 1st argument passed ($1) It should read 1, 2, 3 or 4.
   [LIST]
  [*]If the 1st argument's value is '1' (backup process is begining) it won't do anything, ##Backup starting is just a comment.
  [*]If the 1st argument's value is '2' (backup process has ended) it won't do anything, ##Backup finishing is just a comment.
  [*]If the 1st argument's value is '3' (a new snapshot was taken) the $msg variable gets updated with the value of the snapshot ID and snapshot path, and a flag is raised ($mailmsg takes value='1').
  [*]Similar behaviour in case of an error (1st argument's value will then be '4').
    [/LIST]
[*]Then, if the flag was raised, this is, if an error occured or a snapshot was taken, it will launch the ssmtp program to send out a mail the message $mailmsg
 [/LIST]

You probably could use the whole script, only changing this line:
```
/bin/echo -e $msg | /usr/sbin/ssmtp $address
```
with these two lines
```
/bin/date >> /path/to/logfile
/bin/echo -e $msg >> /path/to/logfile
```

And if you want to go a little further, get rid of the $address variable, and modify $msg varialbe to fit your needs.

---

