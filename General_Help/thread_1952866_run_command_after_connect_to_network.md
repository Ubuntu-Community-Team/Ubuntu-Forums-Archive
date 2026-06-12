---
title: "run command after connect to network"
date: 2012-04-05
forum: General Help
---

### Post by EngMAF on 2012-04-05
hi all
i need to run a sh file every time my labtop connect to a network
how do i accomplish that

---

### Post by kc1di on 2012-04-05
> **EngMAF said:**
> hi all
i need to run a sh file every time my labtop connect to a network
how do i accomplish that
What version of Ubuntu?

---

### Post by EngMAF on 2012-04-05
thanks for ur fast reply
my version is 11.10

---

### Post by kc1di on 2012-04-05
Here is a thread very similar to yours that may give you the info to do it.  I'm at work now and don't have the time to write it all out.  But when your done go to the file manager and click on view <show hidden folders> place the .desktop file you've created in the 
.config/autostart folder and it should run every time you boot into Ubuntu.
good luck 
[http://ubuntuforums.org/showthread.php?t=1886486]("http://ubuntuforums.org/showthread.php?t=1886486")

---

### Post by EngMAF on 2012-04-05
dear kc1di
   thanks for your time

i think you got me wrong
i want to log my currnt ip adress
i have made an sh file that do log the ip adress
now i am using cron job to run that sh file every hour
i am asking how to run that sh only when the pc connected to network 

in other words when the router restarted or the pc restarted the sh file should run

---

### Post by Toz on 2012-04-05
Try creating an executable file in /etc/network/if-up.d with contents like this:
```

#!/bin/bash

# Don't bother to do anything for lo.
if [ "$IFACE" = lo ]; then
	exit 0
fi

# Only run from ifup.
if [ "$MODE" != start ]; then
	exit 0
fi

#your code here....

```

Again, make sure the file is executable.

This script should run every time a network interface comes up.

---

### Post by EngMAF on 2012-04-05
tahnks Toz thats exactly what i need , it works

---

### Post by kc1di on 2012-04-05
> **EngMAF said:**
> tahnks Toz thats exactly what i need , it works

Glad you got it I was mistaken ;)

---

### Post by EngMAF on 2012-04-05
> **kc1di said:**
> Glad you got it I was mistaken ;)
i appreciate your effort :KS

---

