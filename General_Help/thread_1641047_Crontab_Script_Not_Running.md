---
title: "Crontab Script Not Running"
date: 2010-12-08
forum: General Help
---

### Post by th1bill on 2010-12-08
> */2 * * * *  /home/willis/changer
 
#  .---------------- minute (0 - 59) 
#  |   .------------- hour (0 - 23)
#  |   |   .---------- day of month (1 - 31)
#  |   |   |   .------- month (1 - 12) OR jan,feb,mar,apr ... 
#  |   |   |   |  .----- day of week (0 - 6) (Sunday=0 or 7)  OR sun,mon,tue,wed,thu,fri,sat 
#  |   |   |   |  |
#  *   *   *   *  *  command to be executed
I opened "crontab -e" in the Terminal and in nano I copied and pasted the first line of this copied script, leaving all the notated lines out.  Each time I manually run changer by clicking and selecting "Run" it changes my Wallpaper but this does not happen automatically no matter how many times I reboot.

Does anyone know what "Stupid" did to mess up a perfectly good plan?

Any help will be greatly appreciated.

---

### Post by dcstar on 2010-12-08
> **th1bill said:**
> I opened "crontab -e" in the Terminal and in nano I copied and pasted the first line of this copied script, leaving all the notated lines out.  Each time I manually run changer by clicking and selecting "Run" it changes my Wallpaper but this does not happen automatically no matter how many times I reboot.

Does anyone know what "Stupid" did to mess up a perfectly good plan?

Any help will be greatly appreciated.

Cron jobs do not run in the same environment as a user terminal in a logged in graphical desktop.

Do a web search for running cron jobs and specifying the display for GUI apps, there are literally thousands of posts already on this issue.

---

### Post by Crusty Old Fart on 2010-12-13
Putting the red line shown in the code box below, directly beneath the shebang line in my scripts, allows them to run as cron jobs. Maybe it will work for you as well.
```

#!/bin/bash
[SIZE=3]**[COLOR=Red]export DISPLAY=:0.0 # Allows script to run as a cron job[/COLOR]**
[/SIZE] [SIZE=2][COLOR=Green][B][SIZE=3]~~~ Follow with the rest of your code ~~~[/SIZE]
[/B][/COLOR][/SIZE]
```

---

### Post by Cheesehead on 2010-12-13
First, determine if this is a crontab issue or a script issue.

To see if it's a crontab issue, run 'crontab -l' and make sure the crontab is still correct. You don't need to reboot to install a changed user-level crontab, the 'crontab' command takes care of that automatically. It also checks your syntax, and would have given you an error if your crontab line had a common error.

Next, edit your script to do some trivial action if triggered, then see if cron is really running the script. My favorite trivial action is to create/update a dummy file: 'touch /tmp/look-at-me-i-am-a-dummy-file'.

If the trivial action occurs, then your cron and crontab are fine, and you have a script problem.

The most common and likely script problem, as Crusty has said, is a missing environment variable. Cron's environment normally doesn't know which display you use.

For example, I use the following change-background script for XFCE: 
```
FILE=`ls -BS1 $LOCAL_PATH | sort --random-sort | head -1`
DISPLAY=:0.0 sudo -u cheesehead xfconf-query -v -c xfce4-desktop -p /backdrop/screen0/monitor0/image-path -s "${LOCAL_PATH}/${FILE}"
```The important part is on the second line: DISPLAY=:0.0 sudo -u cheesehead
'DISPLAY=:0.0' tells the system to apply it to my laptop screen.
'sudo -u cheesehead' ensures that the following command runs as me, not root - because my script might be triggered at times by one of my root-level jobs (like an Upstart event)

---

