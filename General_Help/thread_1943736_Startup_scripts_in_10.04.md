---
title: "Startup scripts in 10.04"
date: 2012-03-20
forum: General Help
---

### Post by ufarmer on 2012-03-20
Hi,

I have a script that I want to execute automatically on booting.  I thought this was as simple as putting the script in /etc/init.d but this clearly is not working.  I have Googled for the answer but several posts -- recommending several solutions -- haven't worked so far.

Any advice is appreciated.

Regards.

---

### Post by codemaniac on 2012-03-20
So you have a script of your own that you want to run at bootup, each time you boot up , right ?
put the mentioned script(myscript.sh) in the /etc/init.d/ directory.
```
update-rc.d myscript.sh defaults
```

dont forget to turn the execution bits on the script.
```
chmod +x myscript.sh
```

---

### Post by ufarmer on 2012-03-20
Hi,

When I ran

```
update-rc.d myscript.sh defaults
```

I got a complaint about missing LSB information.  After some Googling I found the solution to this and added some header information to my script.  Here is the new script:

```
#! /bin/bash

### BEGIN INIT INFO
# Provides: touchpad
# Required-Start: $local_fs
# Required-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Kill syndaemon then start syndaemon -d -i 2.0
# Description: Kill syndaemon and restart to disable touchpad for 2.0 seconds after each keystroke.
### END INIT INFO

kill `pidof syndaemon`
syndaemon -d -i 2.0
exit 0
```

This has gotten rid of the LSB complaint but the script is definitely not being run after booting (and the script is executable).

Any advice is appreciated.

Regards.

---

### Post by codemaniac on 2012-03-20
So you have modified the script , my dear friend !!
Can you do the following in your terminal ?

```
/etc/init.d$ sudo update-rc.d -f myscript.sh remove
```
```
/etc/init.d$ sudo update-rc.d myscript.sh defaults
```

---

### Post by ufarmer on 2012-03-20
Hi,

Thanks for replying.  I executed those instructions in the correct directory but the script still does not launch on boot.

---

### Post by Zorael on 2012-03-20
```
# Short-Description: Kill syndaemon then start syndaemon -d -i 2.0
# Description: Kill syndaemon and restart to disable touchpad for 2.0 seconds after each keystroke.
### END INIT INFO

kill `pidof syndaemon`
syndaemon -d -i 2.0
exit 0
```

Won't this get run too early in the boot process, before X start?

I'd recommend you make it a script in **/etc/X11/Xsession.d/** instead. Just don't include an exit call since the script will be sourced (and not run normally).

---

### Post by ufarmer on 2012-03-20
Hi,

Thanks for replying.  I tried your suggestion but it still doesn't launch on boot.

---

### Post by Zorael on 2012-03-20
Are you certain it's not being run? **/etc/X11/Xsession** should source it like everything else in there;
```
*[...]*

SYSSESSIONDIR=/etc/X11/Xsession.d

*[...]*

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run-parts --list $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  set +e
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
  set -e
fi
```

Have you tried adding debug statements to your script there? Like, something that writes to a log file so you have proof that it's being read?

**/etc/X11/Xsession.d/99test**;
```
#!/bin/bash

echo "$(date "+%H:%M:%S") Script was run! (well, sourced)" >> /tmp/scriptlog

killall syndaemon
sleep 1
syndaemon -d -i 2.0 &>>/tmp/scriptlog

echo "I did my best!" >> /tmp/scriptlog
```

Does it create a **/tmp/scriptlog**?

---

### Post by ufarmer on 2012-03-20
Things just sort of go crazy when I execute the first code.  My XSession restarts and the terminal prints out a lot of warnings and failures -- particularly about things that are already running.  Eventually it seems to hang as well.

As for the second code, I found nothing in /tmp/scriptlog.

---

### Post by Zorael on 2012-03-20
> **ufarmer said:**
> Things just sort of go crazy when I execute the first code.
Ah, no; apologies for not explaining. I was merely showing how (and where) all files in **/etc/X11/Xsession.d/** should be read and parsed.


I remember there being a Kubuntu bug where none of the Xsession.d scripts were read at all, and the core functionality were instead replicated in scripts in **/etc/kde4/kdm/**. But I thought that was in 11.04 or so and not 10.04.

There's lots you can do to keep debugging this and find the real cause (because that script placed there should be run/sourced, and that log file should be created), but the easy solution is to just place the script in **~/.config/autostart/**. This makes it user-specific though, so you would have to do the same thing for other users.

**~/.config/autostart/syndaemon-voodoo**; (set as executable)
```
#!/bin/bash

killall syndaemon
sleep 1
syndaemon -d -i 2.0
```

---

