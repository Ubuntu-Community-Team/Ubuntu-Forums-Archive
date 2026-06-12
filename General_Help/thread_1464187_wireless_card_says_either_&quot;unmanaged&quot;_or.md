---
title: "wireless card says either &quot;unmanaged&quot; or &quot;disabled&quot;"
date: 2010-04-27
forum: General Help
---

### Post by Tak11 on 2010-04-27
my wireless card on kubuntu works perfectly, until a few weeks later when it for some reason randomly stops working with seemingly no cause. saying either the network manager is "unmanaged" or the wireless card is "disabled", i edited the configuration file in /etc/NetworkManager/ and set the value from false to true, however that didn't work, and reinstalling for the third time is just dodging the issue. 

I'm running on an hp pavilion dv7-3085dx

and an Intel WiFi Link 5100AGN card.

---

### Post by Tak11 on 2010-04-28
bump, please >.< I'm sick of using windows, but ubuntu is unusable with this bug, and I need the help of someone wiser than myself =(

---

### Post by tynen on 2010-04-28
You're not the only one: [http://ohioloco.ubuntuforums.org/showthread.php?p=9060102](http://ohioloco.ubuntuforums.org/showthread.php?p=9060102)

---

### Post by chaosgrimm on 2010-05-10
Try checking these, should be set as:

/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

-------
and

/var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---

### Post by Tak11 on 2010-06-02
> **chaosgrimm said:**
> Try checking these, should be set as:
c

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

-------
and

/var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

:KS

sorry for the late response, I reinstalled for like the 8th time, then the bug came back up. thank you SOOO much, i checked 
/etc/NetworkManager/nm-system-settings.conf before, however not the other file, the combination of the two solved the problem. I'll write a script to check / repair this on startup so it doesn't happen again, and for people who also have this issue.

---

### Post by Tak11 on 2010-06-02
Wrote the script
can be found at:

[http://pastebin.com/raxb300P](http://pastebin.com/raxb300P)

```

#!/bin/bash
#repair interwebs.
#by: tak 6/2/2010

#Repairs occasional networking bug in kubuntu.

ROOT_UID=0  

echo "Checking for root..."

if [ "$UID" -eq "$ROOT_UID" ]  
then
  echo "You are root. moving on"
else
  echo "Run as root."
  exit 1
fi

if [ -n `cat /etc/NetworkManager/nm-system-settings.conf | grep false` ]
then
  echo "Problem found.."
  sed 's/false/true/g' /etc/NetworkManager/nm-system-settings.conf > /etc/NetworkManager/nm-system-settings.temp
  rm /etc/NetworkManager/nm-system-settings.conf
  mv /etc/NetworkManager/nm-system-settings.temp /etc/NetworkManager/nm-system-settings.conf
  echo "Problem repaired."
fi

if [ -z `cat /etc/NetworkManager/nm-system-settings.conf | grep ifupdown,keyfile` ]
then
  echo "Problem found.."
  sed 's/plugins=.*$/plugins=ifupdown,keyfile/g' /etc/NetworkManager/nm-system-settings.conf > /etc/NetworkManager/nm-system-settings.temp
  rm /etc/NetworkManager/nm-system-settings.conf
  mv /etc/NetworkManager/nm-system-settings.temp /etc/NetworkManager/nm-system-settings.conf
  echo "Problem repaired."
fi

if [ -n `cat /var/lib/NetworkManager/NetworkManager.state | grep false` ]
then
  echo "Problem found.."
  sed 's/false/true/g' /var/lib/NetworkManager/NetworkManager.state > /var/lib/NetworkManager/NetworkManager.temp
  rm /var/lib/NetworkManager/NetworkManager.state
  mv /var/lib/NetworkManager/NetworkManager.temp /var/lib/NetworkManager/NetworkManager.state
  echo "Problem repaired."
fi

exit 0


```

---

