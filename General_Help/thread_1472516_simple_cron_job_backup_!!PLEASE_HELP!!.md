---
title: "simple cron job backup !!PLEASE HELP!!"
date: 2010-05-04
forum: General Help
---

### Post by sarah-skyfox on 2010-05-04
i am very sorry if this has been asked before... i'm sure it has.. but i have searched all over the net looking for an answer and i still cant find it... so somebody pleeeeease help me!

I have a really simple cron job script like this:

cd /var/www/vhosts/

tar -cvzf /backup/myhttpdocs-backup-`/bin/date +\%Y\%m\%d`.tar mywebsite.com.au/httpdocs/


when i run this manually it works fine
but when i run it from my ROOT user in Plesk as a cron task is always creates a file that is just 45 bytes. Why doesn't it work... I am running it as a root user.. so surely i must have permission to access the file?!!! Its driving me nuts.

HELP!!!

---

### Post by sarah-skyfox on 2010-05-04
oh yeah and PS... my /backup folder is chmod 777

the full path to the directory i want to backup is:

/var/www/vhosts/mywebsite.com.au/httpdocs/

---

### Post by jwbrase on 2010-05-04
> **sarah-skyfox said:**
> i am very sorry if this has been asked before... i'm sure it has.. but i have searched all over the net looking for an answer and i still cant find it... so somebody pleeeeease help me!

I have a really simple cron job script like this:

cd /var/www/vhosts/

tar -cvzf /backup/myhttpdocs-backup-`/bin/date +\%Y\%m\%d`.tar mywebsite.com.au/httpdocs/


when i run this manually it works fine
but when i run it from my ROOT user in Plesk as a cron task is always creates a file that is just 45 bytes. Why doesn't it work... I am running it as a root user.. so surely i must have permission to access the file?!!! Its driving me nuts.

HELP!!!

I don't think it's a permissions problem. If it weren't for the "cd /var/www/vhosts/" I'd say it was a problem with "mywebsite.com.au/httpdocs/" being a relative address and root and your main user having two different home directories.

As it is, I'm not certain what's causing it, but you might want to try using the full path of "mywebsite.com.au/httpdocs/" instead of just the relative path from your working directory. If it weren't for the "cd ..." line that would certainly be the problem, but the "cd ..." line should make it not matter (unless I'm overlooking something really obvious).

---

### Post by sarah-skyfox on 2010-05-04
does the trailing slash make a difference?

mywebsite.com.au/httpdocs/

maybe i can try like this

mywebsite.com.au/httpdocs

??

---

### Post by jwbrase on 2010-05-04
The trailing slash should make no difference. (I assume that httpdocs is a directory?)

However, I did a test on my own machine, and it turns out that if tar can't find a file that's supposed to go into a *.tar file, it writes the rest of the *.tar and leaves that file out. If it can't find any of the files that are supposed to go into the *.tar, it creates an empty tar file with a length of 45 bytes.

So what's happening is that it's not finding the files it's supposed to back up. So you need to understand what each part of the script tells the computer to do:

```
cd /var/www/vhosts/
```

This tells the computer to change into the /var/www/vhosts/ directory. This makes it so that any filenames it encounters that don't have a *leading* slash will be taken to be subdirectories of /var/www/vhosts/. For example, the computer will read ```
this/is/an/example/
``` as ```
/var/www/vhosts/this/is/an/example/
```

```
tar -cvzf /backup/myhttpdocs-backup-`/bin/date +\%Y\%m\%d`.tar mywebsite.com.au/httpdocs/
```

"Run the program tar, tell it to create a *.tar file (-c), tell you everything that it's doing (-v), compress the tar with gzip (-z), and use the specified filename for the *.tar file (-f /backup/myhttpdocs... blah blah blah). The following directory is to be put into the *.tar file: "mywebsite.com.au/httpdocs/""

Notice that "mywebsite.com.au/httpdocs/" does not have a leading slash. This, combined with the previous "cd" command means that the shell will interpret "mywebsite.com.au/httpdocs/" as "/var/www/vhosts/mywebsite.com.au/httpdocs/". Apparently, "mywebsite.com.au/httpdocs/" is not in "/var/www/vhosts/", but rather in some other directory. So you need to find out what directory "mywebsite.com.au/httpdocs/" is in, and CD to *that* directory, or else put that directory at the beginning of "mywebsite.com.au/httpdocs/".

For example you could either do this:

```
cd /this/is/an/example/

tar -cvzf /backup/myhttpdocs-backup-`/bin/date +\%Y\%m\%d`.tar mywebsite.com.au/httpdocs/
```

Or:

```
tar -cvzf /backup/myhttpdocs-backup-`/bin/date +\%Y\%m\%d`.tar /this/is/an/example/mywebsite.com.au/httpdocs/
```

It could also be that you have a typo somewhere either in "/var/www/vhosts/" or "mywebsite.com.au/httpdocs/". Check to see that everything is spelled correctly.

---

### Post by sarah-skyfox on 2010-05-05
Wow... thankyou so much for all that info....
i have a nasty feeling though that it's something else..

Because i can run this script manually through ssh shell and it works fine!
But when i run the extact same script as a cron task it doesnt work.

I am using Plesk.. and i am running the task as root so i just dont get it... is there some way i can get an error report so i might know what is going wrong?

Thankyou so much for your help

I am running the cron from another file like this

/bin/bash /bin/backupscript.sh 2>&1 >/dev/null

i'm not getting messages in my error log... do i have to change the end bit... ? i have no idea what it means..  2>&1 >/dev/null  ?

---

### Post by sarah-skyfox on 2010-05-05
I solved this by just creating 3 SEPERATE scheduled tasks in Plesk that directly run the commands:

mysqldump --user=admin --password=mypassword --all-databases > /backup/mysqlall-`/bin/date +\%Y\%m\%d`.sql

tar -cvzf /backup/mywebsite.com-backup-`/bin/date +\%Y\%m\%d`.tar /var/www/vhosts/mywebsite.com/httpdocs

AND

find /backup -mtime +5 -exec rm {} \;

Plesk wil run these task fine as root user - when you create them as 3 SEPERATE cron tasks
but if i put them together in a script file and try to cron that only the mysql dump command works - the tar command doesn't... weird right?

Anyhow... i hope this helps anyone who has been going insane like me for the last 2 weeks...
just do it like that and it works fine.

---

### Post by jwbrase on 2010-05-05
> **sarah-skyfox said:**
> Wow... thankyou so much for all that info....
i have a nasty feeling though that it's something else..

Because i can run this script manually through ssh shell and it works fine!
But when i run the extact same script as a cron task it doesnt work.

Yeah, that confuses me too. Is there *anything* else in the script, or is that the whole thing? Anything that might be dependent upon which user you are? For example, does "~/path/to/a/file" show up anywhere? The "~/" means the home directory of the current user, and would be dependent upon which user was logged in.

> 
I am using Plesk.. and i am running the task as root so i just dont get it... is there some way i can get an error report so i might know what is going wrong?

I'm not familiar with Plesk. However, you can get an error report, see below:

> 
Thankyou so much for your help

I am running the cron from another file like this

/bin/bash /bin/backupscript.sh 2>&1 >/dev/null

i'm not getting messages in my error log... do i have to change the end bit... ? i have no idea what it means..  2>&1 >/dev/null  ?

2>&1 >/dev/null tells the computer "Take any output messages or error messages and throw them away". (2>&1 sends standard error to the same place as standard output, > /dev/null throws standard output away).

So you can try putting "2>&1 >/path/to/an/error/log/for/this/script/here" or ">& /path/to/an/error/log", and that should log the errors to whatever file you choose.

---

