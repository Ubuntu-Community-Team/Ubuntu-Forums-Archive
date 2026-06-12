---
title: "Can not get cron jobs to run correctly"
date: 2011-11-20
forum: General Help
---

### Post by *Chris* on 2011-11-20
OS: Ubuntu 10.04 lts

Cron Jobs are not running after being set.

I have tried the following formats however I am still unable to get a cron to run.

0,5,10,15,20,25,30,35,40,45,50,55 * * * * /bin/sh /pathtofile/file
*/5 * * * * /bin/sh /pathtofile/file
/5 * * * * /bin/sh /pathtofile/file
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /pathtofile/file
*/5 * * * * /pathtofile/file
/5 * * * * /pathtofile/file

As well I have also reviewed [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) however I am still unable to get the crons working.

Notes
verified "file" is executable
Tried setting the crons using crontab -e and sudo crontab -e.

Any assistance would be greatly appreciated.

---

### Post by alarme on 2011-11-20
Hi,

At least   */5 * * * * /pathtofile/file    must work

Keep in mind that the output to console is disabled for scripts running in cron (there is no console associated)

To see if your script is really working, you can try this:

1st create a script like this:


#!/bin/bash
echo "It works!"
date

echo "It works!" >> /tmp/myscript.log
date >> /tmp/myscript.log

save as myscript.sh and set permissions:
$ sudo chmod +x myscript.sh

dry run it
$ ./myscript.sh

you get the output to the console plus a log file

now, create the line in crontab

*/1 * * * * /pathtofile/myscript.sh

On screen, you can't see nothing, but if you read /tmp/myscript.log, you can see it grows with two new lines every minute.

Maybe this help you

Cheers

---

### Post by ajgreeny on 2011-11-20
Can you show the script in total;  there are limits to what can run in cron, even if the same script will run in a normal bash environment from terminal, it may not do so when using cron.

Does the script work in terminal?  You did not say so, but I assume you have tried.

---

### Post by gmargo on 2011-11-20
Check the log files.  Cron tells you what it's doing in **/var/log/syslog**.  (You may have to read the older syslog files.)

Most likely you do not have an MTA installed (such as postfix or exim4), so you are not receiving the email that cron is kindly sending to you.

---

### Post by *Chris* on 2011-11-20
> **ajgreeny said:**
> Can you show the script in total;  there are limits to what can run in cron, even if the same script will run in a normal bash environment from terminal, it may not do so when using cron.

Does the script work in terminal?  You did not say so, but I assume you have tried.

Followed steps from alarme however still did not work.

Sorry, I should have put this in my original post however the script does work through terminal and has been tested by the creating a log file. A sample of the log file and my tests (which were manually run) are below with the complete script.

Successful!!! || Sat Nov 19 14:12:11 AST 2011
Successful!!! || Sat Nov 19 14:35:06 AST 2011
Successful!!! || Sat Nov 19 16:12:17 AST 2011
Successful!!! || Sat Nov 19 16:23:48 AST 2011
Successful!!! || Sun Nov 20 03:18:46 AST 2011
Successful!!! || Sun Nov 20 04:58:39 AST 2011

In a nut shell, wget is performed, creates a log file and searches for a 200 code, if the 200 code is not found it should send me  an email.

#!/bin/bash
wget website name -S -o log.txt
rm index.html
lookup=$(grep -q 200 log.txt; if [ $? -eq 0 ]; then echo "Yes"; else echo "No"; fi)

if [ $lookup = "No" ]
then
echo "Not Successful || $(date)" >> completionlog.txt
fi

if [ $lookup = "Yes" ]
then
echo "Successful!!! || $(date)" >> completionlog.txt
fi

if [ $lookup = "No" ]
then sendemail -f [EMAIL="test@test.com"]test@test.com[/EMAIL] -t [EMAIL="test@test.com"]test@test.com[/EMAIL] -u subject of email -a attachedfile -m "body of email"
fi

---

### Post by *Chris* on 2011-11-20
> **gmargo said:**
> Check the log files.  Cron tells you what it's doing in **/var/log/syslog**.  (You may have to read the older syslog files.)

Most likely you do not have an MTA installed (such as postfix or exim4), so you are not receiving the email that cron is kindly sending to you.

Okay so after looking in **/var/log/syslog **I can see the cron is running and it does send an email however it does not create the log.txt file or updates the completionlog.txt file.

Some sort of permissions error but I am unable to figure this out.  Any Ideas?

Thanks

---

### Post by gmargo on 2011-11-20
One idea is:  What directory do you think this script is running in?  Since log.txt and completion.txt are relative pathnames, they are probably "somewhere else" from where you expect them.  Add an explicit "cd" to your preferred directory, or use full pathnames for the files.

---

### Post by *Chris* on 2011-11-20
> ***Chris* said:**
> Okay so after looking in **/var/log/syslog **I can see the cron is running and it does send an email however it does not create the log.txt file or updates the completionlog.txt file.

Some sort of permissions error but I am unable to figure this out.  Any Ideas?

Thanks


When adding the full path to the file in the script, everything started working okay and as designed.

wget website name -S -o /full/path/log.txt


Thanks to everyone.

---

