---
title: "Lucid does not like my Cron Job :("
date: 2010-05-02
forum: General Help
---

### Post by jv2112 on 2010-05-02
When I run this this script in bash it works perfect. When I run as a cron job it starts but never finishes. The reason I know it starts is because a temp file is started by zip but never is completed.

The funny thing I was running Linux Mint 8 and this worked fine I just switched to Ubuntu 10.04 & bang no good ......

:confused:

All Input appreciated. :guitar:


Crontab -l Output -->

# m h  dom mon dow   command
18 21 * * * /home/joe/Scripts/./BU


Script -->

#! /bin/bash
zip -r -9 /media/Abyss/Archive/"Joe--->$(date)".zip /home/joe/
# add -e option to ZIP for encryption -> zip -er (E-Encryption / R- Recursive) /media/Abyss/Archive/Filename.zip  Source Directory/
find /media/Abyss/Archive -name *.zip -amin -1435 -exec cp -a {} /media/Linuxlab/Zip-Redundancy \;
find / -name *Joe*.zip -atime +7 -exec rm {} \;

---

### Post by jv2112 on 2010-05-02
Anyone..... Starting to feel foolish....... Help !!!! :confused::-({|=

---

### Post by happyhamster on 2010-05-02
Perhaps $(date) isn't available for cron's shell?

---

### Post by krismatth3 on 2010-05-02
When the script is in the hung state, does   ```
ps ax | grep zip
```  list anything?

---

### Post by happyhamster on 2010-05-02
Perhaps $(date) isn't available for cron's shell?

[edit: I somehow managed to double-post 40 minutes after my first post? Weird :confused:]

---

### Post by jv2112 on 2010-05-02
joe@Tux-Box:~$ ps ax | grep zip

 3299 pts/0    S+     0:00 grep -i zip


:confused:

How would I tell if the date is not available ?

---

### Post by happyhamster on 2010-05-02
> **jv2112 said:**
> How would I tell if the date is not available ?
For example test if cron runs the script when choosing a fixed filename.

zip -r -9 /media/Abyss/Archive/test.zip /home/joe/

If the script runs in that case, you'll need to somehow set date as an environment variable for cron's shell.

---

### Post by jv2112 on 2010-05-03
I did & no dice :(

---

### Post by tgalati4 on 2010-05-03
What version of bash are you running in each:

bash --version

When running in Minty, what was the user that the process was running as?

When running in Lucid, what is the user that the process is running as?

Sounds like a subtle change in security policy between minty8 and Lucid.

---

### Post by jv2112 on 2010-05-05
GNU bash, version 4.1.5(1)-release (x86_64-pc-linux-gnu)

Me in both I assume.

---

### Post by jv2112 on 2010-05-07
When I tail -f /var/log/syslog


acpid: exiting --> about 1 minute after the job starts killing the job. :mad:

Any Ideas ?

---

### Post by happyhamster on 2010-05-08
> **jv2112 said:**
> acpid: exiting
- acpi takes care of powermanagement. Is this a laptop?

- Just a wild guess: the drive the cronjob is trying to write to is in low-power state (head is parked, etc), and for some reason, powermanagement fails to properly wake it up. Does the job run if you stop acpi beforehand? Run:

sudo service acpid stop

- and see if the job will run. To start acpi again afterwards, run:

sudo service acpid start

- Do you have other cronjobs running?

---

### Post by gmargo on 2010-05-08
> **jv2112 said:**
> 
#! /bin/bash
zip -r -9 /media/Abyss/Archive/"Joe--->$(date)".zip /home/joe/
# add -e option to ZIP for encryption -> zip -er (E-Encryption / R- Recursive) /media/Abyss/Archive/Filename.zip  Source Directory/
find /media/Abyss/Archive -name *.zip -amin -1435 -exec cp -a {} /media/Linuxlab/Zip-Redundancy \;
find / -name *Joe*.zip -atime +7 -exec rm {} \;

My guess is the lack of quoting on the wildcard entries.

*.zip should be '*.zip'

*Joe*.zip should be '*Joe*.zip'

Also, whatever "Joe--->$(date)" is supposed to mean: it's always a bad idea to use a redirection character as part of a filename.

---

### Post by jv2112 on 2010-05-08
Tried both killing daemon & changing naming conventions.  Still works when I run manually but not as a cron job :(

:mad:

---

### Post by dcstar on 2010-05-08
> **jv2112 said:**
> Tried both killing daemon & changing naming conventions.  Still works when I run manually but not as a cron job :(

:mad:

As has been repeated in many other posts of people complaining about cron jobs not working when they do in a user terminal :-

[SIZE="4"]User sessions and cron sessions are **different** environments.[/SIZE]

**Cron jobs should have absolute paths for all file references** and not assume that what is found in a user terminal will be in the search path in the cron environment.

There must be hundreds of posts already just in this forum with similar problems and the solutions.

---

### Post by jv2112 on 2010-05-09
Understood but the same script worked prior with the same crontab files set up prior to 10.04 ---> So something changed there...... 

If you are so confident --> Offer some constructive advice and not a rant... any one can rant..... .... I guess you have nothing to offer.... :mad:

---

### Post by dcstar on 2010-05-10
> **jv2112 said:**
> Understood but the same script worked prior with the same crontab files set up prior to 10.04 ---> So something changed there...... 

If you are so confident --> Offer some constructive advice and not a rant... any one can rant..... .... I guess you have nothing to offer.... :mad:

I just did, have you put **absolute paths** into the commands or are just sulking?

10.04 is **different** to previous releases, just because something worked in a **different** Ubuntu release is no guarantee that it will work now.

---

### Post by jv2112 on 2010-05-10
Yes I have, No Dice. 

On the first page somebody else made the same recommendation.

It does what it originaly did. Start a Temp zip file then does not continue.  Does cron keep a error log somewhere ?


This is very frustrating... :mad:

---

### Post by gmargo on 2010-05-11
Your script must be substantially different now given your debugging efforts.  Please post a copy of your latest script (wrap in CODE tags for best display.)

---

### Post by jv2112 on 2010-05-11
> 

#! /bin/bash
zip -r -9 /hme/joe/Desktop/"Joe--->$(date)".zip /home/joe/
# add -e option to ZIP for encryption -> zip -er (E-Encryption / R- Recursive) /media/Abyss/Archive/Filename.zip  Source Directory/
find /media/Abyss/Archive -name *.zip -amin -1435 -exec cp -a {} /media/Linuxlab/Zip-Redundancy \;
find / -name *Joe*.zip -atime +7 -exec rm {} \;




All Help Appreciated !!!:P

---

### Post by dcstar on 2010-05-11
> **jv2112 said:**
> All Help Appreciated !!!:P

Why are there no absolute paths to **all** of the commands?

You cannot assume that a cron environment will work the same as a user shell.

---

### Post by bredman on 2010-05-11
You may not understand the comment from dcstar...

You cannot use a command like 'zip' in a cron job. You should use an absolute path such as '/bin/zip' instead. Use the command 'which zip' to find the path on your machine.

Similar comment for the find cp and rm commands.

Did you notice that /home/joe is mis-spelled as /hme/joe ?

Did you check that your /media directories actually exist?

And for pity's sake, never use the '>' character as part of a file name. You may have quoted it correctly for the zip command, but it could screw up the find, cp, or rm commands which have to parse the file names.

---

### Post by jv2112 on 2010-05-15
> #! /bin/bash
/usr/bin/zip -r -9 /media/Abyss/Archive/"Joe--$(date)".zip /home/joe/
find /media/Abyss/Archive -name '*.zip' -amin -1435 -exec cp -a {} /media/Linuxlab/Zip-Redundancy \;
find / -name '*Joe*.zip' -atime +7 -exec rm {} \;


Thanks for the input but still no dice. Like before it starts to run zip. You can see a file being started at the destination but just dies.

And still works if run manually...

Is there a place where cron keeps a error log ?

:confused:

---

### Post by kwd on 2010-07-29
Possibly cron does not like the -- in front of $(date).  

If -- is the problem then a log might not do you much good since it sounds like it is "halting" processing instead of stopping processing and giving an error message. 

Try Joe_$(date) instead of Joe--$(date) and see what that does. 


As far as I know you have to create your own error log by redirecting std error to a file if you want a cron job log file.


Good luck.

---

### Post by DaithiF on 2010-07-29
My guess is its this problem:
[http://ubuntuforums.org/showpost.php?p=7954400&postcount=6](http://ubuntuforums.org/showpost.php?p=7954400&postcount=6)
so put MAILTO="" at the top of your crontab

---

### Post by jv2112 on 2010-07-30
DaithiF YOU ARE THE BEST !!!!!!

I have been playing with this for way toooooooooo long and now I can set my jobs.

AWESOME :guitar:\\:D/

---

### Post by phil0stine on 2010-10-24
DaithiF..... outstanding thanks for the tip! (and explaining the problem really helps too)

Made my night!


> **DaithiF said:**
> My guess is its this problem:
[http://ubuntuforums.org/showpost.php?p=7954400&postcount=6](http://ubuntuforums.org/showpost.php?p=7954400&postcount=6)
so put MAILTO="" at the top of your crontab

---

