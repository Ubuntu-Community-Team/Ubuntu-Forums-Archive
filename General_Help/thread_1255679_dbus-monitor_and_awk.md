---
title: "dbus-monitor and awk"
date: 2009-09-01
forum: General Help
---

### Post by spitfire23bc on 2009-09-01
Hi all, I'm trying to write a bash script that will listen for specific events on dbus and run commands depending on those events. I've been using this script (from [http://fpmurphy.blogspot.com/2009/02/dbus-monitor.html]("http://fpmurphy.blogspot.com/2009/02/dbus-monitor.html")) as a template:

```

#!/bin/bash

OJECT="'org.gnome.Tomboy'"
IFACE="'org.gnome.Tomboy.RemoteControl'"
DPATH="'/org/gnome/Tomboy/RemoteControl'"

WATCH1="type='signal', sender=${OJECT}, interface=${IFACE}, path=${DPATH}, member='NoteAdded'"
WATCH2="type='signal', sender=${OJECT}, interface=${IFACE}, path=${DPATH}, member='NoteSaved'"
WATCH3="type='signal', sender=${OJECT}, interface=${IFACE}, path=${DPATH}, member='NoteDeleted'"

dbus-monitor "${WATCH1}" "${WATCH2}" "${WATCH3}" | \
awk '
/member=NoteAdded/ { getline; print "Created note " substr($2,7) }
/member=NoteSaved/ { getline; print "Added note " substr($2,7) }
/member=NoteDeleted/ { getline; print "Deleted note " substr($2,7) }
'

```

On the author's Fedora 10 system, this gives an output whenever a Tomboy note is created, saved or deleted. On Ubuntu 8.10, it gives no output.

dbus-monitor is working correctly: ```

*(snip)*
dbus-monitor "${WATCH1}" "${WATCH2}" "${WATCH3}"

``` 
works fine; it is the pipe to the awk command that kills any kind of output. 

When the output from the dbus-monitor command is saved to a file and the same awk command run on that file, it gives the expected output.

Is there a way to get awk to run commands whilst dbus-monitor is still going, as is the purpose of this script?

---

### Post by spitfire23bc on 2009-09-03
Solved: used gawk instead of awk

---

