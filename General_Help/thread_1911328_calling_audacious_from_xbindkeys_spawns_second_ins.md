---
title: "calling audacious from xbindkeys spawns second instance"
date: 2012-01-18
forum: General Help
---

### Post by vilwarin on 2012-01-18
Hey Forum!

I am trying to get XF86 Multimedia keys running.
I am using xbindkeys to give them meaning:

```
"/usr/bin/audacious2 -f"
XF86AudioNext
```

Now when audacious is already running and I trigger XF86AudioNext a second instance of audacious starts. Subsequent calls (-f/-r/-t) triggered via xbindkeys do not spawn another instance, but affect the second instance.

If I run "/usr/bin/audacious2 -f" from the shell, it does affect the first running instance of audacious and does not spawn a second one.

Now I'd really like to use xbindkeys to send commands to the instance already running. Do you have any idea, why it might pop up a second instance? Or what I could do?

Both instances are started under my username:
here's a ps ux | grep audacious

```
vilwarin   6218 10.6  0.4 202976 17172 pts/4    Sl   23:42   0:00 audacious2 -f
vilwarin   6235 11.6  0.4 202536 16840 ?        Sl   23:42   0:00 audacious2 -f
```

the first one was created when I run "audacious2 -f" on a shell. the second one when triggering XF86AudioNext

They look pretty much identical to me. I just can't figure out why it would spawn a second instance.

---

### Post by vilwarin on 2012-01-19
anybody encountered something like that and got an idea how to avoid this behavior?

---

### Post by vilwarin on 2012-01-21
In case somebody stumbles across the same issue:

The reason a second instance spawns is the DBUS. 

> D-Bus is a message bus system, a simple way for applications to talk to one another. In addition to interprocess communication, D-Bus helps coordinate process lifecycle; it makes it simple and reliable to code a "single instance" application or daemon, and to launch applications and daemons on demand when their services are needed. 
from freedesktop.org

The DBUS sets an enviroment variable called: DBUS_SESSION_BUS_ADDRESS
that looks something like this:

```
echo $DBUS_SESSION_BUS_ADDRESS
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-aq1meuYZSU,guid=170242a2be23f36edb7c195200000031
```

This allows *audacious -f* to pass the *-f* to the correct audacious via it's DBUS interface. 

When executing something from xbindkeys the env is different. I.e. DBUS_SESSION_BUS_ADDRESS is not set. So in order for *audacious -f* to pass the *-f* to the correct DBUS, we need to set this variable.

The DBUS address associated with a certain application can be found with:

**audiocontrol.sh**
```
pid=pidof APPLICATION
cat /proc/$pid/environ | tr '\0' '\n' | grep DBUS | cut -d '=' -f2-
```

With that we can set the env variable with export:

```
export DBUS_SESSION_BUS_ADDRESS=`cat /proc/$pid/environ | tr '\0' '\n' | grep DBUS | cut -d '=' -f2-`
```

So alltogether I wrote a little script that will work for most audioplayers supporting DBUS and the same command line options:

> #!/bin/bash

# Usage
if test $# -lt 1
    then echo "$0 -f/-r/-t"; exit;
fi

audioplayers=( /usr/bin/amarok /usr/bin/audacious2 )

for i in ${audioplayers[*]}
do
    pid=`pidof $i`
    #set dbus address
    export DBUS_SESSION_BUS_ADDRESS=`cat /proc/$pid/environ | tr '\0' '\n' | grep DBUS | cut -d '=' -f2-`
    if [ "$pid" != "" ]
        then `$i $1`; break;
    fi
done

You can add additional audioplayers in the audioplayers array to have the script support them as well.

In .xbindkeysrc I then call this script, and everything works:

**~/.xbindkeysrc**
> "audio_control.sh --play-pause"
XF86AudioPlay

"audio_control.sh --stop"
XF86AudioStop

"audio_control.sh -r"
XF86AudioPrev

"audio_control.sh -f"
XF86AudioNext


Good luck!

--> solved

---

