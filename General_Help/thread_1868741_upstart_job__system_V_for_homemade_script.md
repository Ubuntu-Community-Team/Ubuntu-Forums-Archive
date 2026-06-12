---
title: "upstart job / system V for homemade script?"
date: 2011-10-24
forum: General Help
---

### Post by Bladtman242 on 2011-10-24
Hi :)
I am looking for a little guidance here. 
Any input will be much appreciated, 
be it direct answers to my questions or general help, please do not hold back :)

I am considering writing my own startup/shutdown script.
The script will be using a ramdisk, it is therefore important that it will automatically perform certain clean-up actions on shutdown and reboot. 
(copying files from the ramdisk to the hdd)
I doubt it is of great relevance, but the script will be starting and controlling a minecraft server.

Should I make an upstart job in /etc/init or a script in /etc/init.d synlinked from /etc/rc|2|0|6|.d ?
Or perhaps a third option is better? (/etc/rc.local ?)

As I see it upstart has a few downsides:
If I put a script in /etc/init.d I can make special functions to handle backup etc.
I am not certain how one would go around that in upstart?
a separate script perhaps?

---

### Post by fdrake on 2011-10-24
i suggest you to go with /etc/rc.local or /etc/init.d/rc.local (which starts the /etc/rc.local script), just to play safe with the updates/upgrades, so that they don't interfere with your script. 

How to : [https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

---

### Post by Bladtman242 on 2011-10-25
Is it possible to make that run preceding shutdown/reboot as well?
That is almost more important than running at at startup :)

---

### Post by fdrake on 2011-10-25
> **Bladtman242 said:**
> Is it possible to make that run preceding shutdown/reboot as well?
That is almost more important than running at at startup :)

this should do for you. [http://crunchbanglinux.org/forums/topic/14453/howto-run-local-scripts-on-systemstartup-andor-shutdown/](http://crunchbanglinux.org/forums/topic/14453/howto-run-local-scripts-on-systemstartup-andor-shutdown/)

also notice the file /etc/init.d/rc.local
> 
### BEGIN INIT INFO
# Provides:          rc.local
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:    **[COLOR="Red"] 2 3 4 5[/COLOR]**
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO
.......

you can change the defualt runlevels and customize each one of them .

ps. make sure you backup your original rc.local all the time first.

---

### Post by Bladtman242 on 2011-10-26
Thanks,  think that's how I'll do it.
Just to be clear, when you say "change the default runlevel"
you mean the runlevels for the script to run in right?
rc.-local couldn't actually affect the default runlevel the machine will boot into, am I correct?

EDIT:
Also, since I have you, I should change the Default-Start to something like 2 3 4 5 right? as S is single user level.

And just to clear something up (I haven't been able to find an explanation to this by googling it):
Will the script just run its own start command on the Default-Start runlevels and its stop command on the Default-Stop runlevels?
if so, could custom Defaults be made? Such that a script with the following in its header
#Default-Reboot: 6
#Default-Shutdown: 0

Would run different functions at shutdown and reboot?
(Not that I need this, but I would like to understand these things :) )

---

### Post by fdrake on 2011-10-28
> **Bladtman242 said:**
> Thanks,  think that's how I'll do it.
Just to be clear, when you say "change the default runlevel"
you mean the runlevels for the script to run in right?
rc.-local couldn't actually affect the default runlevel the machine will boot into, am I correct?

the default runlevel is conrolled by /etc/init/rc-sysinit.conf
in this line
```

# Default runlevel, this may be overriden on the kernel command-line
# or by faking an old /etc/inittab entry
[COLOR="Red"]_**env DEFAULT_RUNLEVEL=2**_[/COLOR]

# There can be no previous runlevel here, but there might be old
# information in /var/run/utmp that we pick up, and we don't want
# that

```



> 
EDIT:
Also, since I have you, I should change the Default-Start to something like 2 3 4 5 right? as S is single user level.

each runlevel ah a folder containing the start/kill scrip for each program of the sys. by default in folder /etc/rc2.d/ /etc/rc3.d/ /etc/rc5.d/ /etc/rc5.d/ you have a script (S99rc.local which is a link to /etc/init.d/rc.local) that starts the script in /etc/rc.local.

> 
And just to clear something up (I haven't been able to find an explanation to this by googling it):
Will the script just run its own start command on the Default-Start runlevels and its stop command on the Default-Stop runlevels?
if so, could custom Defaults be made? Such that a script with the following in its header
#Default-Reboot: 6
#Default-Shutdown: 0


each runlevel has their own start/stop script by defauld . to costumozed shutdown you need to add a link(S**rc.local) of the /etc/init.d/rc.local in runlevel 6. Configurinf shutdown runlevel is a little tricky because you will need to make your script run at first before the shutdown is complete otherwise you will not be avle to run at all your script.

> 
Would run different functions at shutdown and reboot?
(Not that I need this, but I would like to understand these things :) )

rebbot is runlevel 0 , shutdown is 6.

ps . if you want to do a prank to someone change the default runlevel to 0. the sys will rebbot every min non stop!! :D

---

