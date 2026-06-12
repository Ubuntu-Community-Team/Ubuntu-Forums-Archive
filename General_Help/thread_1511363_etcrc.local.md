---
title: "/etc/rc.local"
date: 2010-06-16
forum: General Help
---

### Post by nmobrien4 on 2010-06-16
So I'm running lucid on a macbook pro and I added a few lines to /etc/rc.local to get the fans working properly. The fans work fine until I suspend/hibernate the computer and then turn it back on. I really know nothing about the /etc/rc.local file and was just following advice from someone else's thread. Can anyone clue me in to why this is happening and/or suggest a new method of setting a minimum fan speed that will survive suspend/hibernate?

---

### Post by bodhi.zazen on 2010-06-16
What thread are you following and what problem are you having ?

To edit /etc/rc.local :

```
gksu gedit /etc/rc.local
```and add in your commands (above exit 0 )

---

### Post by nmobrien4 on 2010-06-16
Thanks for the reply. I can't seem to find the original thread. I added this to the file:

```
sudo echo 4000 > /sys/devices/platform/applesmc.768/fan1_min
sudo echo 4000 > /sys/devices/platform/applesmc.768/fan2_min
```


The computer used to run very hot before I added the above lines to /etc/rc.local. When I restart the computer the temperature is fine, but when I suspend/hibernate the computer and resume using it the modified fan settings are not in effect any more and it becomes very hot again. I hope that answered your questions.

---

### Post by bodhi.zazen on 2010-06-16
> **nmobrien4 said:**
> Thanks for the reply. I can't seem to find the original thread. I added this to the file:

```
sudo echo 4000 > /sys/devices/platform/applesmc.768/fan1_min
sudo echo 4000 > /sys/devices/platform/applesmc.768/fan2_min
```The computer used to run very hot before I added the above lines to /etc/rc.local. When I restart the computer the temperature is fine, but when I suspend/hibernate the computer and resume using it the modified fan settings are not in effect any more and it becomes very hot again. I hope that answered your questions.

I would add those commands to a script

```
mkdir ~/bin
```Put this in the script (name the scrip whatever you want, hot.sh if you like):

```
#!/bin/bash

echo 4000 > /sys/devices/platform/applesmc.768/fan1_min
echo 4000 > /sys/devices/platform/applesmc.768/fan2_min
```And call the script with 

sudo ~/bin/hot.sh

If you wish, you can modify sudo so that sudo does not require a password to run that script.

---

### Post by nmobrien4 on 2010-06-16
Thanks for the advice. Seems to be working now :)

---

