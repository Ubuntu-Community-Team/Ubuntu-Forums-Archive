---
title: "Cron Enable?"
date: 2011-03-28
forum: General Help
---

### Post by Atamisk on 2011-03-28
I was just curious if cron had to be enabled before use. i have a crontab, and the cron daemon is running, but the command isn't executing...

---

### Post by MrEgg on 2011-03-28
> **Atamisk said:**
> I was just curious if cron had to be enabled before use. i have a crontab, and the cron daemon is running, but the command isn't executing...

Is your command in /etc/crontab (system wide) or in your userspace's crontab, which you access through crontab -e ?

system wide : no permissions required.
userspace : if you don't have /etc/cron.allow or /etc/cron.deny, it should work. If you have those 2 files, check them to see if you're declared in /etc/cron.allow.

Additionally, it is possible that the command does not execute because of a problem with the crontab entry.

---

### Post by galorin on 2011-03-28
What's the cron job?

Does the un-cronned command work corectly?

---

### Post by Rikeshar on 2011-03-28
I was hoping I could help with this as well?

In crontab -e I have:

```

# This crontab will run the tectonicus script at 5am every morning.

0 5 * * * /usr/bin/tectonicus

MAILTO=zthornbury@gmail.com


```It doesn't seem to be executing though. If I just enter that pathname in the terminal, the script works fine, so I know it's not something to do with that. I tried setting the time to a few minutes out of my current time, so I could see if it even tried to do anything, and it's not. I then went and added it to

# /etc/crontab

and put in

```

20 11   * * *   root    /usr/bin/tectonicus

```and still nothing. (11:20 was a few minutes of when tried it. I don't see where there's any crontab.allow or crontab.deny files in etc.

Any ideas? The times specified in the crontab use system time, and not something like UTC, right?

---

### Post by Cheesehead on 2011-03-28
Test that cron is working:

1) Open /var/log/syslog in any text editor.

2) Cron runs an hourly script, and logs it to the syslog. Look for it in the past hour (bottom of the log). If it's there, then Cron is running.
```
Mar 27 17:17:01 yourhostname CRON[4095]: (root) CMD (   cd / && run-parts -
-report /etc/cron.hourly)

```

---

### Post by Rikeshar on 2011-03-29
It looks like it is:

```

Mar 27 02:17:01 Zach-Ubuntu CRON[5579]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 03:17:01 Zach-Ubuntu CRON[5766]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 04:17:01 Zach-Ubuntu CRON[5953]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 05:17:01 Zach-Ubuntu CRON[6142]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 06:17:01 Zach-Ubuntu CRON[6338]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 06:25:01 Zach-Ubuntu CRON[6367]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Mar 27 06:47:02 Zach-Ubuntu CRON[6433]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))
Mar 27 07:17:01 Zach-Ubuntu CRON[6533]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 07:30:01 Zach-Ubuntu CRON[6575]: (root) CMD (start -q anacron || :)
Mar 27 07:30:01 Zach-Ubuntu anacron[6578]: Anacron 2.3 started on 2011-03-27
Mar 27 07:30:01 Zach-Ubuntu anacron[6578]: Normal exit (0 jobs run)
Mar 27 08:17:01 Zach-Ubuntu CRON[6727]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 27 09:17:01 Zach-Ubuntu CRON[7200]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

The script I'm trying to run, which, as I said, works fine if I manually start it, is:

```

#!/bin/bash
# Script for running Tectonicus Deep Render maps. 

scp -r LOGIN@SERVER:~/minecraft/world ~/Desktop

cd /usr/games

java -jar Tectonicus_v1.30.jar worldDir=~/Desktop/world outputDir=~/Tectonicus Map cameraAngle=225 imageFormat=jpg minecraftjar=~/.minecraft/bin/minecraft.jar playersInitiallyVisible=false signs=all signsInitiallyVisible=false useBiomeColours=true 

rm -rf ~/Desktop/world

```

... where the login and server are replaced with the proper stuff.

---

### Post by bodhi.zazen on 2011-03-29
The most common problem people have with cron is that they do not use the full path.

cron runs with a minimal shell with minimal environmental variables.

In your script, use 

/usr/bin/scp and not scp

use /home/user_name and not ~

and on throughout the script.

Also, is there a way you can run the script without having to use the "cd" command ?

---

### Post by Rikeshar on 2011-03-29
Ah, okay, I'll give it a try and see what happens. Also, I'm not sure if I can... do I not have to be in the same directory as the java file in order to run it as I am?

*EDIT* aha, I can. I've removed the CD from the script. Going to give it a try.

**EDIT EDIT**

AHA! I think it worked. The folder which should be downloaded from the server just showed up on my desktop. Thank you very much!

---

### Post by Rikeshar on 2011-03-29
Hrm. It appears I was too hasty. Cron still isn't running the full script. It seems to download the file, skip running the java program, and then delete the file. 

Can you see anything here as to why that would happen?

```

#!/bin/bash
# Script for running Tectonicus Deep Render maps. 

/usr/bin/scp -r zach0242@SERVERIP:/home/zach0242/minecraft/world /home/thornbury/Desktop

java -jar Tectonicus_v1.30.jar worldDir=/home/thornbury/Desktop/world outputDir=/home/thornbury/Tectonicus cameraAngle=225 imageFormat=jpg minecraftjar=/home/thornbury/.minecraft/bin/minecraft.jar playersInitiallyVisible=false signs=all signsInitiallyVisible=false useBiomeColours=true 

rm -rf /home/thornbury/Desktop/world

```

This script is located at /usr/bin/tectonicus, and if I just type that in to the terminal, it all runs just fine.

---

### Post by Machete on 2011-03-29
The script looks fine, Rikeshar, and Java is actually running - Tectonicus is just crashing. The problem is that the $DISPLAY environment variable isn't set in the cron job. Try either setting the $DISPLAY environment variable in the script (ugly), or setting it in the crontab command line, like this:
```

# This crontab will run the tectonicus script at 5am every morning.

0 5 * * * DISPLAY=:0.0 /usr/bin/tectonicus


```

Just make sure the ":0.0" matches the desired X server $DISPLAY. In your case, it sounds like you can probably just go to a Terminal, and type 'echo $DISPLAY' and substitute the results.

It's been working just fine since I put that in my crontab.

---

### Post by Rikeshar on 2011-03-29
Hrm... I tried that, and I also added a line so that the crontab would put a log file on my desktop. When it ran, I noticed the log file show up on my desktop, but not the world file which the script should have been pulling from the sever. I checked the log and it showed Tectonicus running with the "Level dat not found" which means that Tectonicus ran, but couldn't find the world file, which apparently never was pulled from the server 

:-/

I'm not quite sure why parts of the script would be running but not others. If I start the script manually, everything works just fine.

**EDIT** Display=:0.0 wouldn't work, but :0 did. :)

---

### Post by RedScourge on 2011-05-03
I am posting this here incase someone coming here runs into the issue that I did, which took me days to figure out!

If you are using scripts named something like script.sh and they are in  folders such as /etc/cron.hourly, make sure you modify your /etc/crontab  (or /etc/anacrontab) file or they will not run!!!

  For example, in /etc/crontab:
   
1 * * * * root cd /tmp && run-parts --report /etc/cron.daily
   
Change to:
   
   1 * * * * root cd /tmp && run-parts --regex='(.*)' --report /etc/cron.daily


Unlike some other systems like RedHat/Fedora/etc, run-parts under Debian  or Ubuntu systems will ignore files with dots or most other characters  in their name, meaning some or all of your scripts in run-parts folders  such as /etc/cron.daily will not be run. For example  /etc/cron.daily/backup.sh will never be run with the default way that  /etc/crontab is set up.
  
  From man cron:
  
  "Files must conform to the same naming convention as used by  run-parts(8): they must consist solely of upper- and lower-case letters,  digits, underscores, and hyphens. If the -l option  is specified, then  they must conform to the LSB namespace specification, exactly as in the  --lsbsysinit option in run-parts."

---

