---
title: "Nothing happens when ACPI power state changes"
date: 2009-08-27
forum: General Help
---

### Post by mjwalfredo on 2009-08-27
I have been on a quest to reduce the power consumption on my laptop so I tried to implement some scripts that are supposed to be exectud on startup, resume, unplugging and plugging.

It seems as though they will only run when I execute them manually.  I found out about /var/log/acpid so I checked it out only to find that the last log entry is from Mar. 20.  WTF?

Do you think the lack of messages in the log is because no events are registering with acpid or because logging is just turned off?

Also, is there any way I can manually watch /proc/acpi/events to see if it is actually sending messages to acpid?

---

### Post by mjwalfredo on 2009-08-27
acpid's man page says that it is supposed to log ALL of its activities and all of the stdout and stderr from any activities to syslog. I am getting nothing in the acpid log or syslog.

I am able to start up acpi_listen and I see that acpid is catching the events.  Hmm...

---

### Post by mjwalfredo on 2009-08-27
I feel like I am talking to myself here....
Well, I am excited because this stuff seemed so mysterious at first but it's actually pretty simple.

My problem was that I got these scripts from this thread : [http://ubuntuforums.org/showthread.php?t=847773]("http://ubuntuforums.org/showthread.php?t=847773")
and the name of the script is 99-savings.

I was able to figure out that power.sh gets executed when the power state changes.  In the script, it only executes scripts ending with the .sh extension.  Problem solved.

I've still got one little problem.  I want the power.sh script to execute the scripts when I resume from standby.  I put in some debugging "echo" statements and it looks like the script is exiting at checkStateChanged; statement.  I am not exactly sure how that works but I am thinking about removing it so that the scripts get always get executed when power.sh runs.  Is that a good idea? Is there a way to get my scripts to run when resuming from suspend but not for every single event that acpid catches?

Here is my power.sh script as it is currently:

```
#!/bin/bash
# TODO:  Change above to /bin/sh

test -f /usr/share/acpi-support/key-constants || exit 0

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getState;

checkStateChanged;

shopt -s nullglob

for x in /proc/acpi/ac_adapter/*; do
    grep -q off-line $x/state

    if [ $? = 0 ] && [ x$1 != xstop ]; then	
	for SCRIPT in /etc/acpi/battery.d/*.sh; do
	    . $SCRIPT
	done
    else
	for SCRIPT in /etc/acpi/ac.d/*.sh; do
	    . $SCRIPT
	done
    fi
done 

```

---

