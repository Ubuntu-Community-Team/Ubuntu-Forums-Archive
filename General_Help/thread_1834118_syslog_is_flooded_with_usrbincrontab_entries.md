---
title: "syslog is flooded with /usr/bin/crontab entries"
date: 2011-08-27
forum: General Help
---

### Post by Ubunky on 2011-08-27
Hi all,

I'm running Ubuntu 10.04. I recently tried to create a cronjob in my user's crontab which executes a bash scipt every 10 minutes by using ***Applications --> System Tools --> Scheduled tasks***

Directly after saving the cronjob I've noticed that my syslog file is flooded with "*/usr/bin/crontab*" messages every 9 seconds.

It looks like this:
```
Aug 25 21:10:01 rechner CRON[2260]: (ubunky) CMD (/home/ubunky/scripts/test.sh >/dev/null 2>&1 # JOB_ID_1)
Aug 25 21:10:03 rechner /usr/bin/crontab[2269]: (ubunky) LIST (ubunky)
Aug 25 21:10:12 rechner /usr/bin/crontab[2273]: (ubunky) LIST (ubunky)
Aug 25 21:10:21 rechner /usr/bin/crontab[2277]: (ubunky) LIST (ubunky)
Aug 25 21:10:30 rechner /usr/bin/crontab[2281]: (ubunky) LIST (ubunky)
Aug 25 21:10:39 rechner /usr/bin/crontab[2285]: (ubunky) LIST (ubunky)
Aug 25 21:10:48 rechner /usr/bin/crontab[2289]: (ubunky) LIST (ubunky)
Aug 25 21:10:57 rechner /usr/bin/crontab[2296]: (ubunky) LIST (ubunky)
Aug 25 21:11:06 rechner /usr/bin/crontab[2322]: (ubunky) LIST (ubunky)
Aug 25 21:11:15 rechner /usr/bin/crontab[2326]: (ubunky) LIST (ubunky)
Aug 25 21:11:24 rechner /usr/bin/crontab[2330]: (ubunky) LIST (ubunky)
Aug 25 21:11:33 rechner /usr/bin/crontab[2334]: (ubunky) LIST (ubunky)
Aug 25 21:11:42 rechner /usr/bin/crontab[2338]: (ubunky) LIST (ubunky)
Aug 25 21:11:51 rechner /usr/bin/crontab[2342]: (ubunky) LIST (ubunky)
Aug 25 21:12:00 rechner /usr/bin/crontab[2346]: (ubunky) LIST (ubunky)
Aug 25 21:12:01 rechner CRON[2350]: (ubunky) CMD (/home/ubunky/scripts/test.sh >/dev/null 2>&1 # JOB_ID_1)
... etc.
```

What are these "LIST" messages and why do they appear every 9 seonds? As the PC runs the whole day this would mean a very big syslog file, wouldn't it?

Do you know a way to suppress these messages? Have I done sth. wrong?

---

### Post by gmargo on 2011-08-27
> **Ubunky said:**
> 
```
Aug 25 21:10:01 rechner CRON[2260]: (ubunky) CMD (/home/ubunky/scripts/test.sh >/dev/null 2>&1 # JOB_ID_1)
Aug 25 21:10:03 rechner /usr/bin/crontab[2269]: (ubunky) LIST (ubunky)

```What are these "LIST" messages and why do they appear every 9 ....

The "LIST" message appears if one does a "crontab -l" command.  Are you doing that from your cron script?  If not I wonder if the system's "Scheduled tasks" thing is a process trying to helpfully "monitor" the crontab file?

---

### Post by Ubunky on 2011-08-27
Hi gmargo,

thanks for your help. :)

> The "LIST" message appears if one does a "crontab -l" command. Are you doing that from your cron script?

No. I'm basically using gconftool-2 within the script to change the standby time period under certain conditions. Btw. the scripts name isn't "test.sh". I've just changed it here in the code tags for paranoid reasons ;). Just in case you suspect it interferes with the systems test command.

Even if I would have "crontab -l" in the bash script wouldn't this mean the LIST message would appear only all 10 minutes just like the cronjob executes the script and not every 9 seconds?

> If not I wonder if the system's "Scheduled tasks" thing is a process trying to helpfully "monitor" the crontab file? 

As far as I understand it, the "Scheduled tasks" thing is just an editor to the users crontab file. Why would it do a "crontab -l" every 9 seconds?

---

### Post by gmargo on 2011-08-27
I'm trying to follow what you did, so I booted up 10.04 Lucid with the default Ubuntu desktop (Gnome based), but I can't find ***"Applications --> System Tools --> Scheduled tasks"*** .  What desktop are you using? Or where does this menu come from?

---

### Post by Ubunky on 2011-08-27
I'm using Gnome 2.30.2. I think you have to install "gnome-schedule" from the repository as it's not part of a basic install.

---

### Post by Habitual on 2011-08-27
anybody else notice the "rechner" user and the "/home/ubunky/scripts/test.sh" in the cron definition?

how about the OP post the contents of /home/ubunky/scripts/test.sh?

---

### Post by gmargo on 2011-08-27
> **Habitual said:**
> anybody else notice the "rechner" user and the "/home/ubunky/scripts/test.sh" in the cron definition?

I don't understand that.  "rechner" is the host name.  "ubunky" is the user name.

---

### Post by Ubunky on 2011-08-27
> I don't understand that.
Me neither. Where's the problem? As gmargo says one's the hostname the other my username.

> how about the OP post the contents of /home/ubunky/scripts/test.sh? 

Sure, no problem.

```
#!/bin/bash

# Function for running gconftool-2 in cronjob. Details http://ubuntuforums.org/showthread.php?p=9109780
export_variables () {
	user=$( whoami )
	pid=$( pgrep -u $user gnome-panel )

	for dbusenv in $pid; do
		DBUS_SESSION_BUS_ADDRESS=$( grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//' )

		data="DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS"
		eval " export $data"
	done
}

# Call function
export_variables

# Read current standby time period
StandbyTime=$(gconftool-2 -g /apps/gnome-power-manager/timeout/sleep_computer_ac)

# Check for .lock file
if [ -f /medien/.lock ]; then
  if [ $StandbyTime -eq 0 ]; then
    exit 0
  else
    /usr/bin/gconftool-2 --type int --set /apps/gnome-power-manager/timeout/sleep_computer_ac 0 >/dev/null 2>&1
  fi
# .lock doesn't exist
else
  if [ $StandbyTime -eq 3600 ]; then
    exit 0
  else
    /usr/bin/gconftool-2 --type int --set /apps/gnome-power-manager/timeout/sleep_computer_ac 3600 >/dev/null 2>&1
  fi
fi
```

---

### Post by gmargo on 2011-08-27
> **Ubunky said:**
> I'm using Gnome 2.30.2. I think you have to install "gnome-schedule" from the repository as it's not part of a basic install.

Thank you for pointing me at that.

As soon as I opened **gnome-schedule** through Applications -> System Tools -> Scheduled tasks, I started getting LIST hits in the log, every 9 seconds, just like you did.

As soon as I closed the **gnome-schedule** window, those LIST hits stopped.  Do you have it running?

---

### Post by Ubunky on 2011-08-28
> As soon as I closed the gnome-schedule window, those LIST hits stopped.

OMG, gmargo you're a genius :mrgreen:. You're absolutely right. The "LIST" messages every 9 seconds are a result of the running gnome-schedule screen. As soon as I quit it, the messages stop. I wouldn't have figured that out in a million years. 

Thanks for all the work you put in and your help.

Cheers
Martin

---

