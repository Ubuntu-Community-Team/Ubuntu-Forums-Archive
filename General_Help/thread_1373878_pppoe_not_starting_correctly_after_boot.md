---
title: "pppoe not starting correctly after boot"
date: 2010-01-06
forum: General Help
---

### Post by andanotherthrowawayuser on 2010-01-06
I've configured my dsl with pppoeconf and have checked the option to connect on boot. After that script has run the connection works. When I restart it does not. If I then type
```
sudo poff -a && pos dsl-provider
```it works again.

It annoies me to have to type this at every start up. I can't just put it in a script because of the sudo command. Does anyone have an idea how I can automatically execute this command as root at the end of each boot or how to make it work in the first place?

---

### Post by andanotherthrowawayuser on 2010-01-06
does no one have an idea?

---

### Post by inf-h4x0r on 2010-01-06
run these commands as root

First, create a script
```
nano /etc/init.d/SCRIPT_NAME
```Second, edit script content
```

#!/bin/sh
sudo pon dsl-provider

```Third, add execute permission
```
chmod +x /etc/init.d/SCRIPT_NAME
```Fourth, update init.d for add new script on startup
```
update-rc.d SCRIPT_NAME defaults
```then reboot your system for test.
[COLOR=Red]attention:[/COLOR] after the reboot may you get [this problem]("http://ubuntuforums.org/showthread.php?p=8620480")!

---

