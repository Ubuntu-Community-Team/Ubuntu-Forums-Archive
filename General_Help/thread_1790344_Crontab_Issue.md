---
title: "Crontab Issue"
date: 2011-06-24
forum: General Help
---

### Post by xImpul5e on 2011-06-24
Hi, I am trying to run a very simple script via crontab but it fails with exit status #1 according to the syslog file. However, when I run the crontab as root, it fails with exit status #127.

Here is the crontab entry (user level, not root): ```
0 5 * * * /home/george/World_mapper/Render.sh
```(Yes, there is an extra line at the bottom)

And here is the Render.sh script it is pointing to: ```
#!/bin/bash
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-openjdk/jre/bin/java"
MANDATORY_PATH="/usr/share/gconf/gnome.mandatory.path"
LOGNAME="george"
SHELL="/bin/bash"
# end of configuration

DISPLAY=:0.0 java -jar /home/george/World_mapper/Tectonicus_v2.02.jar config=Config.xml

```As you can see, I have set up the java environment variables in the script, however it still fails to execute.

The script runs fine from the terminal which leads me to believe its a crontab environment problem. However, the java environment seems to be setup correctly and I am stumped.

Here is the java version information if that helps: ```
java version "1.6.0_20" OpenJDK Runtime Environment (IcedTea6 1.9.8) (6b20-1.9.8-0ubuntu1~10.10.1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)
```Any help at all with this would be much appreciated.

---

### Post by Toz on 2011-06-24
EDIT: sorry, wrong info.

---

### Post by xImpul5e on 2011-06-24
> **Major_Bloodnok said:**
> Crontab is NOT a bash shell.
To fix, edit  /etc/crontab , make SHELL=/bin/bash, NOT /bin/sh

Secondly, install "gnome schedule" - an outstanding GUI to crontab.
Big thank you to the creator, Gaute Hope.

Next your "command" in gnome schedule maybe this : 
env DISPLAY=0.0  /usr/lib/jvm/java-6-openjdk/jre/bin/java -jar /home/george/World_mapper/Tectonicus_v2.02.jar config=Config.xml

Crontab is pure JOY, when it works; and it does. :D

Thank you for your help.

Unfortunately, changing the SHELL variable in /etc/crontab to /bin/bash did NOT solve the problem. The crontab still fails with exit status 1.

Also, I installed gnome schedule like you recommended, and I agree, it is a great tool. However after inputting your "command", the crontab STILL failed with exit status 1.

Here is the command I inputted into gnome schedule for reference: ```
env DISPLAY=0.0  /usr/lib/jvm/java-6-openjdk/jre/bin/java -jar /home/george/World_mapper/Tectonicus_v2.02.jar config=Config.xml
```And here is the error in the syslog file as well:

```
Jun 24 22:12:01 G-ThinkServer cron[1128]: (george) RELOAD (crontabs/george)
Jun 24 22:12:01 G-ThinkServer CRON[3971]: (george) CMD (env DISPLAY=0.0 /usr/lib/jvm/java-6-openjdk/jre/bin/java -jar /home/george/World_mapper/Tectonicus_v2.02.jar config=Config.xml # JOB_ID_1)
Jun 24 22:12:01 G-ThinkServer CRON[3970]: (CRON) error (grandchild #3971 failed with exit status 1)
Jun 24 22:12:01 G-ThinkServer CRON[3970]: (CRON) info (No MTA installed, discarding output)
```Again, any help would be much appreciated.

---

### Post by Ozymandias_117 on 2011-06-24
Have you tried running the script on it's own?  Based on the output, it seems like the file isn't running properly. If you have, and it works fine outside of cron, try to pipe the output into a file so you can inspect it for anything else.  Also, sh vs bash shouldn't matter, sh is simply a symlink to bash (At least it is on my system).

---

### Post by xImpul5e on 2011-06-24
> **Ozymandias_117 said:**
> Have you tried running the script on it's own?  Based on the output, it seems like the file isn't running properly. If you have, and it works fine outside of cron, try to pipe the output into a file so you can inspect it for anything else.  Also, sh vs bash shouldn't matter, sh is simply a symlink to bash (At least it is on my system).

Thanks for the reply.

Yes, the script works fine outside of cron with no errors at all. And how would I go about putting the output into a file? Could you give me instructions how to do that?

Again, thanks for the help.

---

### Post by Ozymandias_117 on 2011-06-25
Assuming this is the correct code for your cron job still, just change it to:
```
0 5 * * * /home/george/World_mapper/Render.sh >> ~/Desktop/cronLog.txt
```

That will create a file on your desktop called cronLog.txt with any output that command gave.

---

### Post by xImpul5e on 2011-06-25
> **Major_Bloodnok said:**
> To crontab, it appears that you have two issues : 
1) the DISPLAY of the result and 
2) the OUTPUT of your script.

Work on getting issue 2) first.
Redirect the output of your script to a file.

Render.sh
#!/bin/bash
/usr/lib/jvm/java-6-openjdk/jre/bin/java -jar  /home/george/World_mapper/Tectonicus_v2.02.jar config=Config.xml  >> /home/george/output01


"Command" in gnome schedule maybe this :
bash /home/george/World_mapper/Render.sh

When I did this, the folder "output01" was empty after the crontab was run. The crontab still failed with exit status 1.

Any other suggestions? Thanks for the help.
> **Ozymandias_117 said:**
> Assuming this is the correct code for your cron job still, just change it to:
```
0 5 * * * /home/george/World_mapper/Render.sh >> ~/Desktop/cronLog.txt
```That will create a file on your desktop called cronLog.txt with any output that command gave.

The TEXT output that this generated was completely normal. It looked exactly the same when I ran it from terminal. However, the cron job is STILL failing with exit status 1 according to the syslog.

The text output was the ONLY thing generated. The program did not generate any other files like it was supposed to. When I took out the "redirect output" part from the crontab(so now it looks like this): ```
0 5 * * * /home/george/World_mapper/Render.sh
```the Render.sh script still did not do anything(exit status 1). It still does work from terminal though.

I hope that was clear, it's kind of hard to explain.

Any other suggestions? Thanks for the help so far.

---

### Post by xImpul5e on 2011-06-25
> **Major_Bloodnok said:**
> When you run the script manually, what specifically is the output you get on the terminal, for example an application window opens,...files are created in folder abcxyz,...text appears in terminal ? 
Plse be specific.

The output i get when running the script manually is all in the terminal. There is no other application window that opens, it is run only in the terminal (no gui). Image files are also generated in a dropbox folder in my home directory "/home/george/Dropbox".

That is what's **supposed** to happen when running it from crontab. I should get a text output in the terminal with the description of those image files being generated, and those images should appear in my dropbox folder in my home directory.

**EDIT:** The problem has been solved! I'm not really sure how I fixed it though. I found the log file that the java program generated and it said there was an error initializing the display. So i changed the Render.sh script and REMOVED the DISPLAY=:0.0 line and ran the crontab again. It still didn't work, BUT now it said no display was found. I then put that display line back into Render.sh and it finally worked. Nothing actually changed in the Render.sh script, but I'm not complaining!

Thanks to all of you for helping though. I will definitely come back here if I have another question.

**EDIT 2:** Turns out it was a very simple issue which I should have realized sooner. The line in Render.sh that points to the "Config.xml" did not specify the directory the config file was in (even though it was the SAME directory as the script & the java program!) I assumed it was not required but I was unfortunately wrong.

Thanks again for all of your help.

---

