---
title: "SH script works but CRON job fails"
date: 2011-11-17
forum: General Help
---

### Post by rkillcrazy on 2011-11-17
Here's a strange one that I've not been able to figure out...

I have a shell script that I can run with a sudo command and it backs up a **PHPBB3 [MySQL] database** and the raw files from **/var/www/phpbb3**.  The issue is that I can run this via **sudo ./backup.sh** & it'll work just fine.  However, if I let the cron job do it, it'll partially fail.  The DB backs up fine but the tarball creation always fails.  The listing from CRONTAB is also below.  Any help would be great.  The only thing I can think of is I need to add a sudo in front of the tarball creation but if that's the case, I'll have to create another user and add him to the "sudo doers" list so he can run things without being prompted with a password.  I'd rather not go that route and I also figured cron jobs were already being executed as root anyway so I didn't think that was needed.

[SIZE="3"]**Script:**[/SIZE]
**Script's permissions:** -rwx------ 1 root    root    1158 2011-11-15 13:57 backup.sh

```

#!/bin/bash

## Variables
dbuser=root
dbpass=MyPasswordHere
db1name=phpbb3
data1=/var/www/phpbb3
tarball1=phpbb1
dest=/mnt/fs1/phpbb1
logs=/mnt/nas1/bu_logs

## DB1 backup
mysqldump --opt -u $dbuser -p$dbpass $db1name > $dest/$db1name.sql

if [ $? = 0 ];
        then
                echo "The $db1name database backup completed successfully with error code: $?.  " > $logs/$HOSTNAME.log
        else
                echo "There may have been issues.  The database backup exited with error code: $?.  " > $logs/$HOSTNAME.log
fi

echo -e "\r" >> $logs/$HOSTNAME.log

## Data1 backup
tar -cvhzf /$dest/$tarball1.tar.gz $data1


if [ $? = 0 ];
        then
                echo "The backup of $data1 completed successfully with error code: $?.  " >> $logs/$HOSTNAME.log
        else
                echo "There may have been issues.  The data backup exited with error code: $?.  " >> $logs/$HOSTNAME.log
fi

echo -e "\r" >> $logs/$HOSTNAME.log

## List directory contents
ls -hog $dest/$tarball1.tar.gz | cut -d' ' -f3- >> $logs/$HOSTNAME.log
echo -e "\r" >> $logs/$HOSTNAME.log
ls -hog $dest/$db1name.sql | cut -d' ' -f3- >> $logs/$HOSTNAME.log

```

[SIZE="3"]**crontab:**[/SIZE]
0 0 * * * /home/homenet/backup.sh

---

### Post by Lars Noodén on 2011-11-17
What kind of errors are showing up in /var/log/syslog?

---

### Post by Slim Odds on 2011-11-17
CRON does not run "as you", so it does not have the same path, etc.

Put the full path for mysqldump, etc.

Or set the path in the script

---

### Post by CharlesA on 2011-11-17
> **Slim Odds said:**
> CRON does not run "as you", so it does not have the same path, etc.

Put the full path for mysqldump, etc.

Or set the path in the script

I was just about to mention that.

I try to use the full path whenever I am writing scripts.

---

### Post by rkillcrazy on 2011-11-17
> **Slim Odds said:**
> CRON does not run "as you", so it does not have the same path, etc.

Put the full path for mysqldump, etc.

Or set the path in the script

Sorry, I forgot to add the logging.  I echo some minor logging out to a text file.  It might not be great but it at least lets me know if a general failure too place.  The only thing that actually **does work** is the database backup.

[SIZE="3"]**My log file (not /var/log/syslog):**[/SIZE]
```


The phpbb3 database backup completed successfully with error code: 0.  

There may have been issues.  The data backup exited with error code: 1.  

156K Nov 17 00:00 /mnt/fs1/phpbb1/phpbb1.tar.gz

234K Nov 17 00:00 /mnt/fs1/phpbb1/phpbb3.sql

```

---

### Post by rkillcrazy on 2011-11-17
> **Lars Noodén said:**
> What kind of errors are showing up in /var/log/syslog?

I changed the job to run every 2 minutes.  The job takes less than a minute to run manually so it shouldn't be an issue.

**[SIZE="3"]/var/log/syslog:[/SIZE]**
```

Nov 17 15:40:01 phpbb1 CRON[12474]: (root) CMD (/home/homenet/backup.sh)
Nov 17 15:42:01 phpbb1 CRON[12488]: (root) CMD (/home/homenet/backup.sh)
Nov 17 15:44:01 phpbb1 CRON[12501]: (root) CMD (/home/homenet/backup.sh)

```

---

### Post by CharlesA on 2011-11-17
Try adding the full path to tar and see what happens.

---

### Post by rkillcrazy on 2011-11-18
> **CharlesA said:**
> Try adding the full path to tar and see what happens.

I changed the script so **tar** is now **/bin/tar** and still no joy.

---

### Post by CharlesA on 2011-11-18
Ok, then tell cron to redirect the output somewhere so you can see what error is showing up.

Add this after the entry in the crontab:
```
 > /path/to/some/file 2>&1
```

And check that file for errors.

---

### Post by rkillcrazy on 2011-11-18
> **CharlesA said:**
> Ok, then tell cron to redirect the output somewhere so you can see what error is showing up.

Add this after the entry in the crontab:
```
 > /path/to/some/file 2>&1
```

And check that file for errors.

I'm on vacation for the next couple weeks so my replies may be few & far between but I'll add that bit of code and report back.

---

### Post by CharlesA on 2011-11-18
> **rkillcrazy said:**
> I'm on vacation for the next couple weeks so my replies may be few & far between but I'll add that bit of code and report back.
That should narrow it down. Good luck!

---

### Post by rkillcrazy on 2011-11-30
> **CharlesA said:**
> That should narrow it down. Good luck!

I'm not entirety sure what I'm looking for but I do have a log file to look at.  I've zipped it up and attached it.

The funny thing is that I have it scheduled for every 5 minutes - just to test with, and it works fine with that bit of extra code in crontab.  What was that code??  It looked like some sort of a redirect but I'm not sure exactly what it was redirecting.  Smells like awesome-sauce! :P

---

### Post by Lars Noodén on 2011-12-01
You might want to re-check the attachment.  It seems to contain the contents of /var/www and no logs.

---

### Post by rkillcrazy on 2011-12-01
> **Lars Noodén said:**
> You might want to re-check the attachment.  It seems to contain the contents of /var/www and no logs.

Well, like I said, I didn't know what I was looking at.  This is the line of code, from crontab, that creates that txt file: ```
0 0 * * * /home/homenet/backup.sh > /home/homenet/backup.txt 2>&1
```

Was that not what I was supposed to do with that bit of code?

---

### Post by CharlesA on 2011-12-01
Huh, it should have captured all the output of the script, not just the tar portion.

---

### Post by rkillcrazy on 2011-12-01
> **CharlesA said:**
> Huh, it should have captured all the output of the script, not just the tar portion.

So, now what?  I still find it hard to believe that redirecting the output to the log file made it start working.  :confused:

---

### Post by CharlesA on 2011-12-01
> **rkillcrazy said:**
> So, now what?  I still find it hard to believe that redirecting the output to the log file made it start working.  :confused:

Dunno why it just randomly started working after adding the redirect.

Have you taken it out and see if it fails again?

---

### Post by rkillcrazy on 2011-12-01
> **CharlesA said:**
> Dunno why it just randomly started working after adding the redirect.

Have you taken it out and see if it fails again?

Without that redirect, I get a general error and the tarball is smaller and the file is broken/corrupt.


**With that redirect:**
```

The phpbb3 database backup completed successfully with error code: 0.  

The backup of /var/www/phpbb3 completed successfully with error code: 0.  

[COLOR="Red"]2.2M[/COLOR] 2011-12-01 13:46 /mnt/fs1/phpbb1/phpbb1.tar.gz

260K 2011-12-01 13:46 /mnt/fs1/phpbb1/phpbb3.sql

```

**Without that redirect:**
```


The phpbb3 database backup completed successfully with error code: 0.  

There may have been issues.  The data backup exited with error code: 1.  

[COLOR="red"]160K[/COLOR] Dec  1 13:44 /mnt/fs1/phpbb1/phpbb1.tar.gz

260K Dec  1 13:44 /mnt/fs1/phpbb1/phpbb3.sql

```

---

### Post by CharlesA on 2011-12-01
So strange.

I guess just leave the redirect and not worry about it.

By chance, does commenting out the second bit of error checking with a # after removing the redirect allow the tar operation to complete?

---

### Post by fdrake on 2011-12-01
@rkillcrazy : I would check the backup data and find out if the error redirection really worked! I don't think so.. I think some files might be missing due to permission issues
instead of using crontab command (which executes commands only as the user who creates them) to launch your script why don't you add a line to the system crontab file(which lets you choose as which user the script should be run)? you said you need sudo command to run the script, then make the script being launched from root. 
```

echo "
># m h dom mon dow user  command
>0 0    * * *   root    /home/homenet/backup.sh
>" >> /etc/crontab

```

@CharlesA:  I think the reason why is "working" with no errors is because the redirection command is interfering with the value of $?.  So when you check $? 's value in the script you are referring to the redirection command to the log file not the actual tar commands $? value!

basically is like writing:
```

[COLOR="RoyalBlue"]tar -cvhzf /$dest/$tarball1.tar.gz $data1 [/COLOR][COLOR="Red"] > /path/to/some/file 2>&1[/COLOR]
if [ $? = 0 ];
        then .....and so on..

```
correct me if i am wrong...

to get the full error msg and standart outout u should do:
"command 2>&1 log_file"     or     "command &> log_file"

---

### Post by CharlesA on 2011-12-01
That might work too.

When troubleshooting problems with cronjobs, I have always just redirected the entire output of the cronjob to a file from the crontab itself.

---

### Post by rkillcrazy on 2011-12-02
> **fdrake said:**
> @rkillcrazy : I would check the backup data and find out if the error redirection really worked! I don't think so.. I think some files might be missing due to permission issues
instead of using crontab command (which executes commands only as the user who creates them) to launch your script why don't you add a line to the system crontab file(which lets you choose as which user the script should be run)? you said you need sudo command to run the script, then make the script being launched from root. 
```

echo "
># m h dom mon dow user  command
>0 0    * * *   root    /home/homenet/backup.sh
>" >> /etc/crontab

```

First off, this is "sudo's" crontab; not mine.  I don't know if that makes a difference but I read, somewhere, that there's a scrontab for each user.  While logged in with my user, I can run: **crontab -l** and I'll get nothing.  In fact, it'll tell me there's no crontab for the user.  If I log in as the sudo user (sudo su) and do the same command, the job is in there.  So, wouldn't that lead you to believe the job, being run from the sudo-user's crontab, is indeed running under the user with the highest permissions?

Secondly, when I change the line in crontab from: ***/05 * * * * /home/homenet/backup.sh** to ***/05 * * * * root /home/homenet/backup.sh**, the job never seems to actually run.  Using **tail -f /var/log/syslog**, I can see the job trying to fire off every 5 minutes but as near as I can tell, nothing ever happens, as none of the files are generated or touched in any way.

Another thing....  I have webmin installed on this server too.  I don't use it for much of anything but it's there if I ever have questions about certain things.  In this case, I looked at the scheduled cron jobs and that job **is** set to run as root.

---

### Post by CharlesA on 2011-12-02
The job is being run with root permissions, yes. I use that when I do backups so that I can copy permissions.

You could rewrite the script like this:

```
#!/bin/bash

## Variables
dbuser=root
dbpass=MyPasswordHere
db1name=phpbb3
data1=/var/www/phpbb3
tarball1=phpbb1
dest=/mnt/fs1/phpbb1
logs=/mnt/nas1/bu_logs

## DB1 backup
mysqldump --opt -u $dbuser -p$dbpass $db1name > $dest/$db1name.sql && echo "DB Backup Completed OK" > $logs/$HOSTNAME.log || echo "DB Backup Failed to Complete" > $logs/$HOSTNAME.log

echo -e "\r" >> $logs/$HOSTNAME.log

## Data1 backup
tar -cvhzf /$dest/$tarball1.tar.gz $data1 && echo "Data Backup Completed OK" > $logs/$HOSTNAME.log || echo "Data Backup Failed to Complete" > $logs/$HOSTNAME.log

echo -e "\r" >> $logs/$HOSTNAME.log

## List directory contents
ls -hog $dest/$tarball1.tar.gz | cut -d' ' -f3- >> $logs/$HOSTNAME.log
echo -e "\r" >> $logs/$HOSTNAME.log
ls -hog $dest/$db1name.sql | cut -d' ' -f3- >> $logs/$HOSTNAME.log
```

---

### Post by rkillcrazy on 2011-12-02
> **CharlesA said:**
> The job is being run with root permissions, yes. I use that when I do backups so that I can copy permissions.

You could rewrite the script like this:

```
#!/bin/bash

## Variables
dbuser=root
dbpass=MyPasswordHere
db1name=phpbb3
data1=/var/www/phpbb3
tarball1=phpbb1
dest=/mnt/fs1/phpbb1
logs=/mnt/nas1/bu_logs

## DB1 backup
mysqldump --opt -u $dbuser -p$dbpass $db1name > $dest/$db1name.sql && echo "DB Backup Completed OK" > $logs/$HOSTNAME.log || echo "DB Backup Failed to Complete" > $logs/$HOSTNAME.log

echo -e "\r" >> $logs/$HOSTNAME.log

## Data1 backup
tar -cvhzf /$dest/$tarball1.tar.gz $data1 && echo "Data Backup Completed OK" > $logs/$HOSTNAME.log || echo "Data Backup Failed to Complete" > $logs/$HOSTNAME.log

echo -e "\r" >> $logs/$HOSTNAME.log

## List directory contents
ls -hog $dest/$tarball1.tar.gz | cut -d' ' -f3- >> $logs/$HOSTNAME.log
echo -e "\r" >> $logs/$HOSTNAME.log
ls -hog $dest/$db1name.sql | cut -d' ' -f3- >> $logs/$HOSTNAME.log
```


OK, I've tweaked mine and set the job to run every 2 minutes and it's failing.  The logs stays, "Failed to Complete."  I'm sure those double pipes (||) have something to do with that but what do they do???  I've also ran the script with a sudo command, after I made those changes and it worked fine.  Again, I think the issue is with contab not liking something about that script...

Run with sudo command:
```

Completed OK

2.2M 2011-12-02 14:31 /mnt/fs1/phpbb1/phpbb1.tar.gz

259K 2011-12-02 14:31 /mnt/fs1/phpbb1/phpbb3.sql

```

Run with crontab:
```

Failed to Complete

168K Dec  2 14:31 /mnt/fs1/phpbb1/phpbb1.tar.gz

259K Dec  2 14:31 /mnt/fs1/phpbb1/phpbb3.sql

```

---

### Post by Lars Noodén on 2011-12-02
> **rkillcrazy said:**
>  I'm sure those double pipes (||) have something to do with that but what do they do??? 

They're logical OR.  Double ampersands (&&) are logical AND.

```

/bin/false || echo False

/bin/true  || echo False

/bin/true  && echo True || echo False
/bin/false && echo True || echo False

```

---

### Post by CharlesA on 2011-12-02
> **rkillcrazy said:**
> OK, I've tweaked mine and set the job to run every 2 minutes and it's failing.  The logs stays, "Failed to Complete."  I'm sure those double pipes (||) have something to do with that but what do they do???  I've also ran the script with a sudo command, after I made those changes and it worked fine.  Again, I think the issue is with contab not liking something about that script...

Run with sudo command:
```

Completed OK

2.2M 2011-12-02 14:31 /mnt/fs1/phpbb1/phpbb1.tar.gz

259K 2011-12-02 14:31 /mnt/fs1/phpbb1/phpbb3.sql

```

Run with crontab:
```

Failed to Complete

168K Dec  2 14:31 /mnt/fs1/phpbb1/phpbb1.tar.gz

259K Dec  2 14:31 /mnt/fs1/phpbb1/phpbb3.sql

```
That's strange. There must be something in the script that it doesn't like but I can't see what.

Try Redirecting the output of tar (without v) and see what errors it is spitting out:

```
tar -chzf /$dest/$tarball1.tar.gz $data1 [COLOR="Red"]2> /home/username/log 2>&1[/COLOR]
```

Replace /home/username/log with the path and filename you want.

---

### Post by rkillcrazy on 2011-12-02
> **Lars Noodén said:**
> They're logical OR.  Double ampersands (&&) are logical AND.

```

/bin/false || echo False

/bin/true  || echo False

/bin/true  && echo True || echo False
/bin/false && echo True || echo False

```

Understood.  I think there's something similar in Windows.  I know I've used **&&** a few times over the years....

---

### Post by rkillcrazy on 2011-12-02
> **CharlesA said:**
> That's strange. There must be something in the script that it doesn't like but I can't see what.

Try Redirecting the output of tar (without v) and see what errors it is spitting out:

```
tar -chzf /$dest/$tarball1.tar.gz $data1 [COLOR="Red"]2> /home/username/log 2>&1[/COLOR]
```

Replace /home/username/log with the path and filename you want.

Ok, made that change.  Current line in the script looks like:

```


tar -chzf /$dest/$tarball1.tar.gz $data1 2> /home/homenet/backup-tarball.txt 2>&1 && echo "Completed OK" > $logs/$HOSTNAME.log || echo "Failed to Complete" > $logs/$HOSTNAME.log

```

Oddly enough, redirecting the output to that TXT file allows the script to work just fine but the TXT file shows nothing when I use CAT to look at it.

---

### Post by CharlesA on 2011-12-02
That makes no sense at all.

Does it run ok, if you just put tar -chzf /$dest/$tarball1.tar.gz $data1 instead of everything else?

---

### Post by rkillcrazy on 2011-12-02
> **CharlesA said:**
> That makes no sense at all.

Does it run ok, if you just put tar -chzf /$dest/$tarball1.tar.gz $data1 instead of everything else?

I know it doesn't make any sense!  :)

Yes, if I remove the the echo statement, it seems to work fine.  Does that make any sense???? :)

---

### Post by rkillcrazy on 2011-12-02
This is just a shot in the dark but you don't think the 2 commands in the script could be stepping on each other's toes, do you?  Meaning, the mysql backup works fine and then it begins to echo out to the log file, "Completed OK" but by the time it gets to that point, the tarball task is also trying to right to that same file?  I know it's a stretch but, like you said, nothing here is making any sense.

---

### Post by CharlesA on 2011-12-02
> **rkillcrazy said:**
> I know it doesn't make any sense!  :)

Yes, if I remove the the echo statement, it seems to work fine.  Does that make any sense???? :)
That makes no sense at all.

I'd just leave it like that then. You'll know if that part ran or not cuz the tar will be around 2MB.

The commands are run in order, so there shouldn't be any "stepping on toes"

---

### Post by rkillcrazy on 2011-12-02
> **CharlesA said:**
> That makes no sense at all.

I'd just leave it like that then. You'll know if that part ran or not cuz the tar will be around 2MB.

The commands are run in order, so there shouldn't be any "stepping on toes"

HA!  I think I got it.  As soon as I changed the code so it echoed out to different txt files, it all started working fine.

New code:
```

#!/bin/bash

## Variables
dbuser=root
dbpass=snip
db1name=phpbb3
data1=/var/www/phpbb3
tarball1=phpbb1
dest=/mnt/fs1/phpbb1
logs=/mnt/nas1/bu_logs

## DB1 backup
mysqldump --opt -u $dbuser -p$dbpass $db1name > $dest/$db1name.sql && echo "Completed OK" > $logs/$HOSTNAME-mysql.log || echo "Failed to Complete" > $logs/$HOSTNAME-mysql.log
# List sql file-size
ls -hog $dest/$db1name.sql | cut -d' ' -f3- >> $logs/$HOSTNAME-mysql.log

## Data1 backup
tar -chzf /$dest/$tarball1.tar.gz $data1 && echo "Completed OK" > $logs/$HOSTNAME-tarball.log || echo "Failed to Complete" > $logs/$HOSTNAME-tarball.log
# List tar file-size
ls -hog $dest/$tarball1.tar.gz | cut -d' ' -f3- >> $logs/$HOSTNAME-tarball.log

```

**Text files:**
_phpbb1-mysql.log_
```
Completed OK
259K Dec  2 16:05 /mnt/fs1/phpbb1/phpbb3.sql
```

_phpbb1-tarball.log_
```
Completed OK
2.2M Dec  2 16:05 /mnt/fs1/phpbb1/phpbb1.tar.gz
```

---

### Post by CharlesA on 2011-12-02
That shouldn't have been the problem, but glad you got it working. :)

---

### Post by fdrake on 2011-12-02
I confess I am a little bit confused too... but I am also glad that it works for you , I think....:confused:. 8|

---

### Post by rkillcrazy on 2011-12-03
Hey, I'll gladly keep troubleshooting.  I have another server that runs a similar script that tars up something in /var/www and makes a backup of a MySQL database so I was going to implement this same fix.  However, like you guys, I didn't think something like this would be the cause of the issue so I'm okay with troubleshooting further.

---

### Post by CharlesA on 2011-12-03
I don't really know how else to proceed.

Perhaps break down the script into the part that always runs (mysqldump) and the part that fails sometimes (tar) and just rewrite it in chunks to see if something is interfering.

---

### Post by rkillcrazy on 2011-12-05
> **CharlesA said:**
> I don't really know how else to proceed.

Perhaps break down the script into the part that always runs (mysqldump) and the part that fails sometimes (tar) and just rewrite it in chunks to see if something is interfering.

Well, I implemented the same fix (dumping to 2 different log files) and that seemed to fix the same issue on the other server I had mentioned.  Like you, I don't know where else to start looking either...  That's why I started the thread.

Before changing the other server's script to use this work-around, I added a few sleep statements in there - trying to (dis)prove the theory about the log file being stepped on by one of the other processes.  Doing so didn't yield any other result so I made the decision to use my work-around.

I'm inclined to leave this alone and call it a quirk, however, if anyone has any good ideas to try, I'm game!

My current (working) script:
```
#!/bin/bash

## Variables
dbuser=root
dbpass=MyPassHere
db1name=phpbb3
data1=/var/www/phpbb3
tarball1=phpbb1
dest=/mnt/fs1/phpbb1
logs=/mnt/nas1/bu_logs

### MySQL backup
## DB1 backup
mysqldump --opt -u $dbuser -p$dbpass $db1name > $dest/$db1name.sql && echo "Completed OK" > $logs/$HOSTNAME-mysql.log || echo "Failed to Complete" > $logs/$HOSTNAME-mysql.log
# List sql file-size
ls -hog $dest/*.sql | cut -d' ' -f3- >> $logs/$HOSTNAME-mysql.log


### Data backup
## Data1 backup
tar -chzf /$dest/$tarball1.tar.gz $data1 && echo "Completed OK" > $logs/$HOSTNAME-tarball.log || echo "Failed to Complete" > $logs/$HOSTNAME-tarball.log
# List tar file-size
ls -hog $dest/*.gz | cut -d' ' -f3- >> $logs/$HOSTNAME-tarball.log

```

---

### Post by CharlesA on 2011-12-05
Aye, might as well leave it if it's working. I have no idea why tar fails when you redirect it to the same file and not when you redirect it to a different file. :(

---

