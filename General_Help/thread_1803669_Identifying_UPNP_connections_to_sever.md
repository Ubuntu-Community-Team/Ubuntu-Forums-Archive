---
title: "Identifying UPNP connections to sever"
date: 2011-07-13
forum: General Help
---

### Post by kempy1000 on 2011-07-13
Hi,

I have a setup with a mythtv backend that streams media via the built in upnp to two xbox 360s. This works perfect at the moment.

However I need a command/script that can identify if either of the two xbox's are connected via upnp.

I need this so that I can have the system auto shutdown if no one is connected using the existing mythtv sleep wake features. (Basically if a script returns 1 then dont shutdown if returns 0 then shutdown.)

Hoping for an end result of:

```

if upnp is connected then
    dont shutdown
else
    shutdown
fi

```

Thanks
Chris

---

### Post by Habitual on 2011-07-13
Are you able to identify the boxes by their MAC address? </hint> :P

---

### Post by mikejonesey on 2011-07-13
```
#!/bin/bash
if [ -z "$(netstat -tn | grep ESTABLISHED | grep 5000)" ]; then
```
maybe? idk what is upnp, if it is on port 5000 like wiki says then the above should work...

---

### Post by Habitual on 2011-07-13
```
(echo >/dev/tcp/localhost/5000) &>/dev/null && echo "UPNP port $i open" || echo "UPNP port $i closed"
```

---

### Post by kempy1000 on 2011-07-14
Thank you to all for the help. This has been solved!

The problem with using:

> **Habitual said:**
> ```
(echo >/dev/tcp/localhost/5000) &>/dev/null && echo "UPNP port $i open" || echo "UPNP port $i closed"
```

was that the port was always open. (I think routers with removable storage communicate with the same upnp...)

Searching for the hint about mac address lead me to learn how to use netstat and nmap (even if these where the wrong path I still learnt!)

The solution is in:

> **mikejonesey said:**
> ```
#!/bin/bash
if [ -z "$(netstat -tn | grep ESTABLISHED | grep 5000)" ]; then
```
maybe? idk what is upnp, if it is on port 5000 like wiki says then the above should work...

I had to modify this though as for some reason the connections where never on port 5000. Always random on very high ports such as 12958. So I just gave the xboxs static IPs then modified the command. Finished result:

```

#!/bin/bash

if [ -z "$(netstat -tn | grep ESTABLISHED | grep 192.168.1.72)" ]
then
        echo "OFFLINE"
else
        echo "ONLINE and Streaming data"
fi

exit 0

``` 

Many thanks for your help.

Chris

---

### Post by Habitual on 2011-07-14
glad it worked out!

---

