---
title: "scheduled task after resume form suspend to disk"
date: 2009-09-26
forum: General Help
---

### Post by hicadsum on 2009-09-26
Hello, I have a problem to run scheduled task after resume from hibernation (suspend to disk):
I would like to record TV broadcast using mencoder at specified time after resume from hibernation. I set to run mencoder using "at" command at time T:

#!/bin/sh
echo "Start recording at HH:MM:"
read beginning
echo "Set record duration in s:"
read duration
echo "mencoder tv:// -tv driver=v4l2:buffersize=64: -ovc lavc -lavcopts vcodec=libxvid:vbitrate=1800:keyint=25:aspect=4/3 -oac mp3lame -vf pp=fd,denoise3d=3:4:6 -ffourcc DIVX -endpos $duration -o test.avi" > /home/hic/Plocha/progr.txt
sudo at $beginning -f /home/hic/Plocha/progr.txt
echo "Recordin from $beginning for $doba s."

This script works properly on running system. Recording begin at specified time "beginning".

Than I set resume from hibernation using script:

#!/bin/sh
echo "Set date and time of recording in format (for example): Sep 21, 2009 20:50:30"
echo "----------------------------------------------------"
echo "months: Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec"

read datum

# to blank/null counter of rtc time to resume from hibernation:

sudo bash -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"

# rtc use UTC, so I have to count it to CEST (difference between UTC and local time is 2 hours = 7200s): UTC=CEST-7200:

# ...seconds from 1.1.1970 to the time of the recording in local time (CEST):

recCEST=`date -u --date "$datum" +%s`

recUTC=$((recCEST-7200))

# now I subtract 2 minutes to get PC some time to start to desktop:  recUTC - 2 min.):

start=$((recUTC-120))

# set UTC time of start of recording subtracted 120s:

sudo bash -c "echo $start > /sys/class/rtc/rtc0/wakealarm"

echo "PC will resume 120s before the start of the recording."

Now I suspend to disc (hibernate).

PC resumes at specified time properly (resumes to desktop in 45s), but recording (mencoder) will not start in the time set with "at" command (in this case 120s after start of resuming). It will starts some 3,5 min. later. I would like to know why! How can I run a task soon after hibernation? Why doesnt atd run task at specified time in this condition? When I set task using first script, shut down PC, start/power on PC, task will run at specified time. What is the the difference between normal start/power on and resume from suspend to disk/hibernation? By the way, task scheduled "manually" in terminal soon after resume using at also starts at specified time properly...
Thanks for help! (I am a newbie and it is really annoying...)

---

