---
title: "Suspend / Sleep / Shutdown / Geez!  Just take 5"
date: 2009-09-07
forum: General Help
---

### Post by Shibblet on 2009-09-07
I usually set my computer up to do video encoding before I go to bed.  If I turn on Suspend after no activity for 30 minutes in my power settings, it suspends when I stop actual interacting with the computer.

What I would like it to do, is suspend after 15 minutes or so, when the system is idle.  Is there anyway to do that?  Ideally, I'd like it to shutdown when the encode is over, but the only GTK Auto-Shutdown I can find is based on a timer.

---

### Post by gradysghost on 2009-09-07
Just to clarify, you're saying that even if you've got video transcoding jobs running, the system will still suspend while those jobs are running?  If so, I understand the problem (running jobs implies activity).

Just to be sure, I want to make sure you've got the settings put right (I know you've probably checked this already, and I don't want to call you stupid; I just want to be absolutely sure we've checked all the silly piddly stuff first).

Go to System -> Preferences -> Power Management or run gnome-power-preferences.  The first option in the "On AC Power" tab should be "Put computer to sleep when inactive for:" and there's a slider for you to set this to whatever you like.  I just want to be sure you've got this set where you want it.

Let me know what the deal is, and I'll help if I can.

---

### Post by Shibblet on 2009-09-07
Exactly.  Since it is a desktop, it only has "On AC Power" settings.  But I have It set for 30 minutes when inactive.  And it suspends after I get up and walk away for 30 minutes.

---

### Post by aesis05401 on 2009-09-07
Are you familiar with the cron system?

---

### Post by Shibblet on 2009-09-07
> **aesis05401 said:**
> Are you familiar with the cron system?

Isn't that the movie with Jeff Bridges where he is beamed into a computer and forced to play video games?  ;)

Nope, what's Cron?

---

### Post by aesis05401 on 2009-09-08
Cron is the system that fires time based events.  I was about to post a desktop icon/cron entry/suspend script from another distro but it is not working on my Jaunty install when fired by cron.  Check back tomorrow, I will post it if I can find the problem.

In the meantime, it will be helpful to know if your encoder exits when it completes the job.  If not, we will need to look at a different metric to trigger the shutdown.

---

### Post by Shibblet on 2009-09-08
It doesn't exit when it's finished encoding.

---

### Post by P4man on 2009-09-08
AFAIK, ubuntu only detects idle by looking at keyboard/mouse activity. Anything else would be tricky to implement, for instance if you'd look at cpu activity, and you got a screensaver running, the screensaver would prevent suspending. 

Anyway, to answer your question; your best bet would be to run some code upon completion of the encode. Most programs have such an option, which program are you using?

---

### Post by Shibblet on 2009-09-08
> **P4man said:**
> AFAIK, ubuntu only detects idle by looking at keyboard/mouse activity. Anything else would be tricky to implement, for instance if you'd look at cpu activity, and you got a screensaver running, the screensaver would prevent suspending. 

Anyway, to answer your question; your best bet would be to run some code upon completion of the encode. Most programs have such an option, which program are you using?

Handbrake

---

### Post by P4man on 2009-09-08
handbrake doesn't seem to run on karmic at the moment, so i can't try it, but isn't there an option somewhere to run a command upon completion ?

If not, perhaps you can consider using the CLI of handbrake and run the shutdown command after the encoding command.

---

### Post by Shibblet on 2009-09-08
I've thought about that, but I'm not one for the terminal.  I no likey, and I've never been able to run a CLI video encoder, it's just too clunky.

---

### Post by P4man on 2009-09-08
> **Shibblet said:**
> I've thought about that, but I'm not one for the terminal.  I no likey, and I've never been able to run a CLI video encoder, it's just too clunky.

Yeah I can understand that. But isnt there a "execute upon completion" or something similar in handbrake ?

---

### Post by aesis05401 on 2009-09-08
After writing this out I realize most people will not want to go to this trouble.  As another poster mentioned, starting the encoder from the command line with a compound statement would be easiest...  However, you could set a bash script triggered to monitor when any metric drops below a certain thresh-hold for a particular process.

This is not really difficult in theory.  Take this command for example:
```

ps -eo %cpu,cmd | grep gcalctool | grep -v grep | cut -c1-2

```

This will give you the first two digits of a cpu reading calculated for process gcalctool (just an example process that I opened at random from the gnome menu).  The cpu reading reported via this method is the cpu time used by the process divided by the total time the process has been alive.  If you want a good idea of the metrics available you can look through the /proc filesystem or the man files for your favorite process examination tools.

Anyhow... You can add a nice touch by creating a desktop launcher that contains a touch command for activating the script.  For my testing purposes I simply added the following to the 'command' field of a new launcher:
```

touch /home/aesis/.sleep-monitor

```

Then add a check for the .sleep-monitor file to the beginning of your bash script with something like :
```

FLAGFILE="/home/aesis/.sleep-monitor"

if [ -f $FLAGFILE ] && <insert ps -eo %cpu test here> ; then 
rm -f $FLAGFILE
<insert other actions here>
else
<exit script>
fi

```

Finally, add a cron job to run every fifteen minutes pointed at your script.  The syntax for your entry should look something like this:
```

0,15,30,45 * * * * /path/to/script

```

Anyhow, I hope you find the solution that is right for you.

---

