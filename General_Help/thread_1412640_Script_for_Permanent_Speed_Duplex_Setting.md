---
title: "Script for Permanent Speed Duplex Setting"
date: 2010-02-21
forum: General Help
---

### Post by ak07 on 2010-02-21
Hi,

I hope someone can help, I've been researching how to set the speed and duplex settings permanent on the nics in my PC.

I have found this script which uses ethtool

#!/bin/sh
ETHTOOL="/usr/sbin/ethtool"
DEV="eth0"
SPEED="100 duplex full"
case "$1" in
   start)
    echo -n "Setting eth0 speed 100 duplex full...";
    $ETHTOOL -s $DEV speed $SPEED;
    echo " done.";;
   stop)
    ;;
esac
exit 0

I have two questions regarding this

[LIST=1]
[*]Is this the best method of permently setting speed and duplex settings?
[*]Using the script above if i wanted to set the settings for more than one nic, for example eth2, eth3 and so on how could I do this using this script?
[/LIST]
Cheers
AK

---

### Post by dcstar on 2010-02-21
> **ak07 said:**
> Hi,

I hope someone can help, I've been researching how to set the speed and duplex settings permanent on the nics in my PC.

I have found this script which uses ethtool

#!/bin/sh
ETHTOOL="/usr/sbin/ethtool"
DEV="eth0"
SPEED="100 duplex full"
case "$1" in
   start)
    echo -n "Setting eth0 speed 100 duplex full...";
    $ETHTOOL -s $DEV speed $SPEED;
    echo " done.";;
   stop)
    ;;
esac
exit 0

I have two questions regarding this

[LIST=1]
[*]Is this the best method of permently setting speed and duplex settings?
[*]Using the script above if i wanted to set the settings for more than one nic, for example eth2, eth3 and so on how could I do this using this script?
[/LIST]
Cheers
AK
[LIST=1]
[*]/etc/rc.local
[*]Don't you see the "eth0" in the script? - work it out.
[/LIST]

---

### Post by ak07 on 2010-02-22
Yes I do see eth0 - thanks

...anyway moving on from your helpful post :-s

Would I need to add to the line DEV="eth0"

DEV="eth0, eth1, eth2, eth3"

or

DEV="eth0"
DEV="eth1"
DEV="eth2"

Cheers
AK

---

