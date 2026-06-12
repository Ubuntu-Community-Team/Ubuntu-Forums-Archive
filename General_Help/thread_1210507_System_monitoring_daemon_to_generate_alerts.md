---
title: "System monitoring daemon to generate alerts"
date: 2009-07-11
forum: General Help
---

### Post by nr0mx on 2009-07-11
Folks, I asked this a while back but got no responses, so here goes again ..

I'm looking for some kind of monitoring daemon to beat the system near-freezes that I've been seeing on my Ubuntu install on a regular basis. These are not due to one particular app, and it's partly due to memory leaks in apps that I won't stop using anytime soon (Firefox etc).

However, in the mean time my rig freezes pretty regularly due to memory/CPU overload.

I'm looking for something that'll ideally do the following:
1. Monitor CPU usage of the system as a whole, and notify me when it hits a user-defined high-water mark.
2. Similarly monitor memory usage.
3. As part of the notification, tell me which app ( or apps ) contribute the max to the CPU/memory usage.
4. At a 2nd high-water mark for CPU/memory, trigger a separate user-defined action ( typically kill the offending process ) as a preemptive measure to having the system freeze.

Do you know of any software that can do this, or something similar, or can be adapted by me to do this ? ( using scripting )

I'm looking for a deamon kind of process that does it's thing unobtrusively in the background and notifies me when required, and not a process like top ( or its derivatives ) where I need to keep an eye on the output.

Appreciate any thoughts or suggestions.

---

### Post by nice_like_rice on 2009-07-11
My suggestion: use crontab to run a script every 5 minutes which alerts you when anything is above the limit?

---

### Post by nice_like_rice on 2009-07-11
Thought about it for a bit, how about this

first ```
crontab -e
```

and add the line
```

0,5,10,15,25,30,35,40,45,50,55 * * * * /home/script.sh

```

where script.sh is

```

USED=`free | tr -s ' ' | sed '/^Mem/!d' | cut -d" " -f3`


if [ $USED -gt 100 ]
	then notify-send "Warning" "Memory usage is $USED"
fi

```

You need to do "sudo apt-get install libnotify-bin" for that notification thing to work (bottom right popup), I would do it in python but I tried last week to get notifications to work with no success... (short of system call)

Just a thought of how such a script could be implemented, I've never programmed in bash before lol so there are probably better ways of doing it. Obviously that would need to be extended quite a bit :)


side note: can you not use "nice" to prevent the freezes? Or a similar program to limit the ram?

---

