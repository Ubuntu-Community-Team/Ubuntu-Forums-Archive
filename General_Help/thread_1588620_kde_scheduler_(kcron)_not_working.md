---
title: "kde scheduler (kcron) not working"
date: 2010-10-05
forum: General Help
---

### Post by andreselsuave on 2010-10-05
Hi there guys!

When I try to schedule a task with kcron, It doesnt work. I installed it with sudo apt-get install kcron. Now it appears in advanced system settings.If I test the task with the run now button the task works correctly. However, when the set time arrives, the task is not performed automatically. I have tried both the personal user cron and the system cron.

By the way, when I try sudo service crond restart, It says service not recognized and when I use sudo contab -e, the file is empty. It should have something since I added an entry in the system's cron in the kde schedule manager.

Hope someone can help, don't want to learn the crontab syntax, I'm lazy hehe.

Andrés

---

### Post by andreselsuave on 2010-10-13
bump

---

### Post by andreselsuave on 2010-10-13
New info. Found this in /var/log/syslog:
```

Oct 13 12:35:01 Andres CRON[2705]: (andres) CMD (kbackup --autobg /home/andres/backup1.kbp)
Oct 13 12:35:01 Andres CRON[2703]: (CRON) error (grandchild #2705 failed with exit status 255)
Oct 13 12:35:01 Andres CRON[2703]: (CRON) info (No MTA installed, discarding output)

```

however, the command works fine if manually executed in a terminal.

Thank you! :D

---

### Post by andreselsuave on 2010-10-13
Even more info. When I schedule a simple touch command, it works perfectly.

---

### Post by wesamly on 2010-10-23
In my case I was tyring to add a php file as cron job, adding it directly into kcron wouldn't show any results. So I created a bash script (let' say: ) myscript.sh , which contains:

```
/usr/bin/php -f /var/www/fullpath/cron.php
```

then add it to kcron and worked just fine,

-make sure files are executable
-and use the full path for any file you call or you work on in the script.

Hope it helps ;)

---

### Post by andreselsuave on 2010-10-23
Thank you :) 

I will try on monday on the computer I have @ work and will post the results :)

---

### Post by purza on 2010-12-12
I am having the same problem.  I'm trying to run a program to set the data bits on the parallel port one minute to turn every other one on then every other one off the next.  [http://bigasterisk.com/projects/parallel/parcon.c](http://bigasterisk.com/projects/parallel/parcon.c)  The only way I can get it to work is to select "Run Now"  and "Sudo" has to be in front of the command.   A terminal window opens up and I have to enter my sudo pwd.  It mysteriously started working until I rebooted at some point.

 ```
#No comment
*/2 * * * *    sudo /home/howard/Programs/./parcon 1h 2h 3h 4h 5h 6h 7h 8h

#No comment
1,3,5,7,9,11,13,15,17,19,21,23,25,27,29,31,33,35,37,39,41,43,45,47,49,51,53,55,57,59 * * * *    sudo  /home/howard/Programs/./parcon 1l 2h 3l 4h 5l 6h 7l 8h
```

---

### Post by purza on 2010-12-12
OK, I figured some of this out from another thread.  [http://ubuntuforums.org/showthread.php?t=102626&page=2](http://ubuntuforums.org/showthread.php?t=102626&page=2)

I opened a konsole and logged in as root by "sudo su" then typed crontab -e.  There weren't any tasks so I pasted the ones above then exited saving to the same file name.

---

### Post by purza on 2010-12-12
Not sure why kcron doesn't work other than I need to run it from the console while logged in as root.

---

### Post by Cheesehead on 2010-12-13
Purza, 

**User-leve**l cron jobs can only do user-level tasks. If you don't need sudo to run the script manually, then it is a user-level task.

**Root-level** cron jobs will do jobs wil root priveleges (you've been warned) unless you specifically limit a job to run as a specific user. If you need to use sudo to run the script manually, then it is a root-level task, and needs to be run (without sudo) from your root crontab.

Does your script normally require sudo to run manually?
Do you really have a folder named '.'? Or is that some kind of a shortcut?

About setting the minutes:
You can use '1-59/2' for all odd numbered minutes (instead of a list) and '0-58/2' for all even-numbered minutes. You can use similar ranges for hours, etc.

Remember that cron jobs run in a limited environment. They don't know any of your environment variables (like your display or stdout) unless you tell them. If it runs manually just fine, but fails from cron, then it's either a malformed crontab line or a missing environment variable in the script.

It's easy to test which. Just put a simple test command at the top of your script (like 'touch /tmp/hey-i-am-a-dummy-file'). If the action occurs, then crontab is fine and your script is the problem. If the action does not occur, then the script was not run at all and your crontab is the problem.

---

### Post by purza on 2010-12-13
Cheeshead (from Wisconsin, i get :)

Thanks for the info.  (I'm fairly new to Linux and it's been a pretty steep learning curve.)  The dir .?  I believe your referring to is ./ which is the c++ program I compiled and trying to get crontab to run.  (Did I mention that I new to C also?)  Well everything I've read is that you need a high level i.e. root access to obtain software control of the parallel port.  So, this would explain why I couldn't run while not root.  I'm confused as to why it ran briefly via the Kcron application and now doesn't run, but having placed the parameters (which I cut and pasted from Kcron) in the root level cron it is working flawlessly.

Again, thanks for the info.

---

