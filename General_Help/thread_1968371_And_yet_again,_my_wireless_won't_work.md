---
title: "And yet again, my wireless won't work"
date: 2012-04-29
forum: General Help
---

### Post by louisgonick on 2012-04-29
I already solved this issues with Oneiric, somehow with Precise everything is back.

Initially, Ubuntu won't recognize my Wifi Card, after using this codes it does:

```
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k
```

Some kind users here assisted me, and provided with this solution: 

Please try this:
Quote:
sudo gedit /etc/rc.local
Change it to:
Code:
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r ath5k
rfkill unblock all
modprobe ath5k 

exit 0
Proofread carefully, save and close gedit. Now do:
Code:
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit

In Oneiric it worked wonders, Ubuntu finnaly worked with the hardware switch of my Wifi Card. After updating to 12.04 the issue is back.

I need to use the three previously mentioned commands to turn my card on EVERYTIME I boot up, which is incredibly annoying. 

Any suggestions are appreciated, does anybody else have this recurring issue?

Thanks.

---

### Post by dino99 on 2012-04-29
my two cents:

- precise use a newer kernel than oneiric, meaning that interal kernel driver may have changed. So using the same workaround here can brake something working.

- it should be a good idea to google around with your wireless chipset + precise

- is there some usefull errors/warnings logged ?

---

### Post by louisgonick on 2012-04-29
> **dino99 said:**
> my two cents:

- precise use a newer kernel than oneiric, meaning that interal kernel driver may have changed. So using the same workaround here can brake something working.

- it should be a good idea to google around with your wireless chipset + precise

- is there some usefull errors/warnings logged ?

Ive been using these three magic commands since Natty and they still work fine with precise, the part involving gedit doesent. 
Hmm.. What do you mean with "some usefull errors/warnings logged ?" 

Thanks. 
Your suggestions are appreciated.

---

