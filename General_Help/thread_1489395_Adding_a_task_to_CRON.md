---
title: "Adding a task to CRON ?"
date: 2010-05-21
forum: General Help
---

### Post by Plasma_NZ on 2010-05-21
ok, have a service which seems to die often..

I'm curious how to add my script that checks if its running and restart it if required...

Im stumped as to how to add it to cron - to check every 20seconds..

is anyone able to help.?

---

### Post by rnerwein on 2010-05-21
hi
cron only knows minutes, hours, .... etc.
for  seconds you can write your own little script:
while : ; do start_your_script & ; wait ; restart_your_script; done &

ciao

---

### Post by Johnneylee on 2010-05-21
The relevant line would be something like this
```
*/20 * * * * /usr/bin/somedirectory/somecommand
```
But that would be minutes. What I suggest is to use/write an upstart script that starts at boot and then checks things out every 20 seconds.

Cheers!

---

### Post by Plasma_NZ on 2010-05-22
Im no good at writing any type of scripts apart from ultra basic scripts.... so im stumped as how to approach this...

---

### Post by Plasma_NZ on 2010-05-22
solved... didnt use cron..

using something more crude..


```
#!/bin/bash
RESTART="/etc/init.d/myscript.service start"
PGREP="/usr/bin/pgrep"
while true
do
    $PGREP mjpg_streamer || $RESTART 
    sleep 20
done
```

---

