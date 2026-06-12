---
title: "Problem with crontab executing script correctly"
date: 2009-12-31
forum: General Help
---

### Post by Nate_is_cool on 2009-12-31
I have a script that every night executes via crontab. The script includes a program called mencoder, to compile videos into one. Thing is that each day I have about a gigs worth of videos and when crontab executes the script it compiles it and ends up being about 700 kbs. When I execute the script from terminal it works correctly. Does crontab not let mencoder finish or what? 

Crontab:

  GNU nano 2.0.9        File: /tmp/crontab.9QYVYN/crontab                       

0 22 * * * /sbin/shutdown -r now
0 23 * * * /etc/uvcdynctrl/dailyn.sh


my script 

cd /home/administrator/Desktop/Feed/cam1
mencoder * -o temp.avi -ovc lavc -nosound -noskip -fps 50
sleep 15
mkdir temp
mkdir `date '+%m-%d-%y'`
mv temp.avi temp
cd temp
cp temp.avi /home/administrator/Desktop/Feed/cam1/`date '+%m-%d-%y'`
cd /home/administrator/Desktop/Feed/cam1/`date '+%m-%d-%y'`
mv temp.avi `date '+%m-%d-%y'`.avi
cd ..
cd temp
mv temp.avi /var/www/ftp_files/daily/cam1
cd ..
rm -r temp
cd /var/www/ftp_files/daily/cam1
mv temp.avi daily.avi
cd /home/administrator/Desktop/Feed/cam1
rm *.avi

This has been stumping me for about a week. I edited crontab to execute early (setting up to do execute dailyn.sh a minite into the future) and it compiled it short, so I know it has to do with crontab. Also I have crontab running as sudo, ex sudo crontab -e


Thanks a bunch

---

### Post by blueridgedog on 2009-12-31
Since it is running as root, I suggest as a first debugging step to reference everything with absolute paths.  From there, I would add log file to mark each step.


So you would get something like:

```
mencoder /home/administrator/Desktop/Feed/cam1/* -o /home/administrator/Desktop/Feed/cam1/temp.avi -ovc lavc -nosound -noskip -fps 50
sleep 15
mkdir /home/administrator/Desktop/Feed/cam1/temp
mkdir /home/administrator/Desktop/Feed/cam1/`date '+%m-%d-%y'`
mv /home/administrator/Desktop/Feed/cam1/temp.avi /home/administrator/Desktop/Feed/cam1/temp
cp /home/administrator/Desktop/Feed/cam1/temp.avi /home/administrator/Desktop/Feed/cam1/`date '+%m-%d-%y'`
mv /home/administrator/Desktop/Feed/cam1/`date '+%m-%d-%y' `date '+%m-%d-%y'`.avi
mv /home/administrator/Desktop/Feed/cam1/temp/temp.avi /var/www/ftp_files/daily/cam1
rm -r /home/administrator/Desktop/Feed/cam1/temp
mv /var/www/ftp_files/daily/cam1/temp.avi daily.avi
rm /home/administrator/Desktop/Feed/cam1/*.avi
```

---

### Post by Seq on 2009-12-31
I haven't had a chance to look at your script yet, but I do have one question:

> **Nate_is_cool said:**
> Also I have crontab running as sudo, ex sudo crontab -e

Why are you using root's crontab instead of yours? Since they are your files in your home directory (assuming you are, uhm, 'administrator')

---

### Post by john newbuntu on 2009-12-31
As a general, when you use the date variable or anything that changes with time, capture it only once.  Also, your program can be simplified as follows.  Make tweaks to this as necessary.  Your program works fine too but it has too many copy and moves.  Also ensure you have error checking to see if commands succeeded or failed.

```

#!/bin/sh

CURRDATE=`date '+%m-%d-%y'`
{
   echo "Starting Mencoder"
   cd /home/administrator/Desktop/Feed/cam1
   mencoder * -o temp.avi -ovc lavc -nosound -noskip -fps 50
   if [ $? != 0 ];
   then
      echo "OOPS. mencorder failed"
      exit 1
   fi
  
   mkdir $CURRDATE
   cp -f temp.avi /var/www/ftp_files/daily/cam1
   mv -f temp.avi $CURRDATE
   echo "Completed Mencoder"
} > /home/administrator/mencoder${CURRDATE}.out 2>&1

exit 0

```

---

### Post by dcstar on 2009-12-31
> **Nate_is_cool said:**
> I have a script that every night executes via crontab. The script includes a program called mencoder, to compile videos into one. Thing is that each day I have about a gigs worth of videos and when crontab executes the script it compiles it and ends up being about 700 kbs. When I execute the script from terminal it works correctly. Does crontab not let mencoder finish or what? 

Crontab:

  GNU nano 2.0.9        File: /tmp/crontab.9QYVYN/crontab                       

**0 22 * * * /sbin/shutdown -r now**
**0 23** * * * /etc/uvcdynctrl/dailyn.sh
..........
Thanks a bunch

So **you** initiate a **reboot** of your machine, then you start off another job while the reboot is still being processed and you wonder why the second job is not finishing?

---

### Post by Nate_is_cool on 2010-01-01
No it reboots at about 10. At 11 it starts the job. Yes it runs the script as root so that no one else can delete the videos. Problem is that mencoder only does about 4kbs worth of videos then just stops.

This problem only arises when the command is ran through crontab. If i run the command from terminal then It works perfectly.

---

### Post by Seq on 2010-01-01
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2003-April/032845.html]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2003-April/032845.html")
> You need to redirect stdout/err to a file or /dev/null; otherwise your
crond/mailer is going to get annoyed after tons of status junk is spit
out, and close the pipe!

Do you get lots of output from your script when you run it manually? That may be causing your issue.

I'd change the line to redirect stdout to a log file. John newbuntu's version of the script appears to do this already.

---

### Post by dcstar on 2010-01-01
> **Nate_is_cool said:**
> No it reboots at about 10. At 11 it starts the job. Yes it runs the script as root so that no one else can delete the videos. Problem is that mencoder only does about 4kbs worth of videos then just stops.

This problem only arises when the command is ran through crontab. If i run the command from terminal then It works perfectly.

Sorry, I misread that.

The cron environment is different from a user environment, you may need to find what is missing (or as the other post mentioned, send the output to something as it may break the cron mailer).

---

### Post by Nate_is_cool on 2010-01-04
Basically, how can I fix this. When run from terminal it shows that its compiling and works perfectly. It also does the same thing when I use "cat" and change the videos to mpgs. Is there a work-a-round to this?  I'm desperate to fix this. Also how is the crontab environment different from the normal environment. When I have crontab execute just mencoder; 0 12 * * * mencoder * temp.avi -ovc (something like that) it does the same thing, just a 4kb video so its not the script its crontab. Is there another way to have scripts execute a specific time? Like a third party program?

---

### Post by Nate_is_cool on 2010-01-04
Beet you to it. Can anacron be used is this scenario?

---

### Post by Nate_is_cool on 2010-01-05
Not sure if this is just a fluke or something but with anacron out of 4 directories worth of videos, the first folder compiles corectly.

Here is what I mean:

administrator@JITTERS-SURV:~/Desktop/Feed/cam1$ cd 01-04
administrator@JITTERS-SURV:~/Desktop/Feed/cam1/01-04-10$
174M    .
administrator@JITTERS-SURV:~/Desktop/Feed/cam1/01-04-10$
administrator@JITTERS-SURV:~/Desktop/Feed/cam1$ cd ..
administrator@JITTERS-SURV:~/Desktop/Feed$ cd cam2
administrator@JITTERS-SURV:~/Desktop/Feed/cam2$ cd 01-04
administrator@JITTERS-SURV:~/Desktop/Feed/cam2/01-04-10$
4.0K    .
administrator@JITTERS-SURV:~/Desktop/Feed/cam2/01-04-10$
administrator@JITTERS-SURV:~/Desktop/Feed/cam2$ cd ..
administrator@JITTERS-SURV:~/Desktop/Feed$ cd cam3
administrator@JITTERS-SURV:~/Desktop/Feed/cam3$ cd 01-04
administrator@JITTERS-SURV:~/Desktop/Feed/cam3/01-04-10$
4.0K    .
administrator@JITTERS-SURV:~/Desktop/Feed/cam3/01-04-10$
administrator@JITTERS-SURV:~/Desktop/Feed/cam3$ cd ..
administrator@JITTERS-SURV:~/Desktop/Feed$ cd cam4
administrator@JITTERS-SURV:~/Desktop/Feed/cam4$ cd 01-04
administrator@JITTERS-SURV:~/Desktop/Feed/cam4/01-04-10$
4.0K    .
administrator@JITTERS-SURV:~/Desktop/Feed/cam4/01-04-10$

The directory of cam1 is closer to the right size than any of the other ones. Explanation?

---

### Post by Nate_is_cool on 2010-01-06
cmon anyone? I tired "at" with no such luck

---

### Post by Seq on 2010-01-06
> **Nate_is_cool said:**
> cmon anyone? I tired "at" with no such luck

You tried with John Newbuntu's script and it does the same thing?

---

### Post by rnerwein on 2010-01-07
hi
first i have to say i agree with newbuntu - errloging make live easyer
second is -> what's the hell is the sleep 15 in your script. does mean that the mencoder runs in the
background ?? seems to me. 15 seconds to make 4kb.
i'am always afraid if i see sleep command in scripts or programms.
the sleep command is the only thing that makes me wonder.
ciao

---

### Post by Nate_is_cool on 2010-01-07
That was there just for testing. it did the same without it. also I changed it to use cat and record in mpgs. but same problem. ill try that other script next

---

### Post by Nate_is_cool on 2010-01-07
> **john newbuntu said:**
> As a general, when you use the date variable or anything that changes with time, capture it only once.  Also, your program can be simplified as follows.  Make tweaks to this as necessary.  Your program works fine too but it has too many copy and moves.  Also ensure you have error checking to see if commands succeeded or failed.

```

#!/bin/sh

CURRDATE=`date '+%m-%d-%y'`
{
   echo "Starting Mencoder"
   cd /home/administrator/Desktop/Feed/cam1
   mencoder * -o temp.avi -ovc lavc -nosound -noskip -fps 50
   if [ $? != 0 ];
   then
      echo "OOPS. mencorder failed"
      exit 1
   fi
  
   mkdir $CURRDATE
   cp -f temp.avi /var/www/ftp_files/daily/cam1
   mv -f temp.avi $CURRDATE
   echo "Completed Mencoder"
} > /home/administrator/mencoder${CURRDATE}.out 2>&1

exit 0

```


wait just use this instead of my entire script or put this in a script then have it run from my old one. I'm pretty confused, I haven't had anything like this yet.

---

### Post by rayiam on 2010-09-21
Have you solved this yet?  I have the identical problem and 3 full days hosing around with it have got me nowhere.

Thanks

Ray

---

