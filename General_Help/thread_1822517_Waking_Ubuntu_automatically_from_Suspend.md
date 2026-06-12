---
title: "Waking Ubuntu automatically from Suspend"
date: 2011-08-10
forum: General Help
---

### Post by JackK3tch on 2011-08-10
Hello,

I'm looking to find a way to schedule my computer to wake up at say 7:00am. Every night before I go to bed, I put my computer into suspend so the fan doesn't wake me (old computer). I can't seem to find a task scheduler that allows me to be able to wake the system.

I've researched and found similar posts yet no solid solutions. Am I just missing something?

As you may see in my profile, I'm new to Ubuntu so forgive me for being a bit of a "noob" here. However, any response would be much appreciated.

---

### Post by MG&amp;TL on 2011-08-10
Scheduled tasks I believe are controlled by something known as 'Cron jobs' Other than that, I don't know. I shall endeavour to find out. :D

---

### Post by MG&amp;TL on 2011-08-10
Apparently if your kernel supports 'apmd' then this will work, but if not it seems be PD impossible.

```
sudo apt-get install apmd
apmsleep 07:00 -s 
```Or, as somebody on the forum said, "tie a magnifying glass to a piece of string to a weight to your mouse. In the morning, the string will heat up from the magnifying glass, snapping, and prodding the mouse with the weight." :D 

Have fun. ;)

---

### Post by JackK3tch on 2011-08-10
Haha the magnifying glass idea could work!

Thank you MG&TL for your input. I'll check for the program. Crossin' my fingers

---

### Post by Toz on 2011-08-10
I came across this script sometime ago. Don't remember the source. 
```
#!/bin/bash

# Auto suspend and wake-up script
#
# Puts the computer on standby and automatically wakes it up at specified time
#
# Written by Romke van der Meulen <redge.online@gmail.com>
#
# Takes a 24hour time HH:MM as its argument
# Example:
# suspend_until 9:30
# suspend_until 18:45
# suspend_until 0325
# suspend_until 515

# (just drag the scriptfile into terminal window and add time to the line)

# ------------------------------------------------------
# Argument check
if [ $# -lt 1 ]; then
	echo "Usage: suspend_until HH:MM"
fi

# Check whether specified time today or tomorrow
DESIRED=$((`date +%s -d "$1"`))
NOW=$((`date +%s`))
if [ $DESIRED -lt $NOW ]; then
	DESIRED=$((`date +%s -d "$1"` + 24*60*60))
fi


# Define hours/mins/sec to wake-up (for printing purposes only):
hours=$(((DESIRED-NOW)/3600))
minutes=$((  ((DESIRED-NOW)-(hours*3600))/60  ))
seconds=$(( ((DESIRED-NOW)-((hours*3600)+(minutes*60)))  ))

# Kill rtcwake if already running
sudo killall rtcwake

# Let user know what we're going to do
echo "Going to suspend for $hours h $minutes min"

echo "To cancel, press Ctrl+c within the next 10 seconds."
sleep 10

# Set RTC wakeup time
sudo rtcwake -l -m on -t $DESIRED &

# feedback
echo "Suspending..."

# give rtcwake some time to make its stuff
sleep 2

# then suspend
sudo pm-suspend
# -------------------------------------------------------------------------------------
# Any commands you want to launch after wakeup can be placed here
# Remember: sudo may have expired by now

# Wake up with monitor disabled
# xset dpms force off

# Set volume level and (just in case) unmute system
amixer -c 0 set Master 80% unmute
amixer -c 0 set PCM 70% unmute

# echo "Good morning"

# Open VLC (vlc + path to your audio/video file)
vlc '/home/USER/Music/audiofile.mp3'

# Unload rtcwake if it's running, otherwise next time computer won't wake up from sleep
SERVICE='rtcwake'
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE running, killing process..."
    sudo killall rtcwake
else
    echo "$SERVICE is not running, no action taken."
fi

```

---

### Post by MG&amp;TL on 2011-08-10
that looks interesting, how does it wake itself up exactly? Is it turning the speakers on?

I suggest that you probably want to make an alias for the suspend command so that it does this instead of 'just' suspending. Otherwise you may have a LOT of typing to do!

---

### Post by Toz on 2011-08-10
It uses rtcwake (have a look at the man file for a description: **man rtcwake**). I can't remember where I found the script, probably here on ubuntuforums - lol), but the person wanted to be woken up by the computer and have it play a sound - hence the part at the end.

---

### Post by luispotro on 2012-04-22
Worked for me! Thanks

---

### Post by Rodney9 on 2012-05-10
For date and time

sudo rtcwake -m mem -t `date +%s -d"2011-01-11 07:30"`


For everyday at 4:30 I use 

sudo rtcwake -m mem -t `date +%s -d"tomorrow 04:30"`

Rodney

---

### Post by iburroughs on 2012-11-29
Apparently on some systems mine included the system clock is set to UTC then converted to local time for display. This script only works correctly for me if I use:

sudo rtcwake -u -m no  -t $DESIRED &

Also there is a good [explanation]("http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password") of how to run a script which uses sudo without you having to actually put in your password when the system wakes up.
[http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password]("http://askubuntu.com/questions/155791/how-do-i-sudo-a-command-in-a-script-without-being-asked-for-a-password")

---

