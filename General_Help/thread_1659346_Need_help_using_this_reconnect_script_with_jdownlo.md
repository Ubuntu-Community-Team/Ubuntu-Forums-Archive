---
title: "Need help using this reconnect script with jdownloader"
date: 2011-01-03
forum: General Help
---

### Post by geo909 on 2011-01-03
EDIT: Question removed; I wrote a small howto below.

---

### Post by geo909 on 2011-01-03
For anybody who's interested, this is a quick 'n dirty solution to get jdownloader to reconnect using an external script. That would be useful if you don't have a router (for instance you are in a public place) or if you by principle don't want 3d party applications to be able to access your router (I'm sure that the jdownloader guys are trustworthy of course)!  

[LIST=1]
[*]install macchanger
```
sudo apt-get install macchanger
```
[*]Copy the following to a file named reconnect.sh 

```

#!/bin/bash
#reconnect.sh script

sudo ifconfig eth0 down
sudo macchanger -r eth0
sleep 4
sudo ifconfig eth0 up
```

Use wlan or wlan0 instead of eth0 if you use wireless.


[*]Do ```
chmod +x reconnect.sh
``` in a terminal
[*]Run jdownloader as **root**.
[*]Go to Settings->Modules->Reconnection and select the *External* tab
[*]In the command field, write */usr/bin/sudo*
[*]In the parameter box write two lines: 
```

sh
/absolute/path/to/reconnect.sh

```
[/LIST]

That should make jdownloader to reconnect automatically.

Hope that helps somebody, if you have any better solution (especially one that doesn't require jdownloader to be run as root) please let me know.

---

### Post by harishsudharsan on 2012-03-22
Works Perfectly.

---

