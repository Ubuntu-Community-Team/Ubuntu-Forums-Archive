---
title: "No wired network after standby"
date: 2010-04-28
forum: General Help
---

### Post by Leppie on 2010-04-28
Weird issue with my nic.
Last night I made a patch to connect my box directly to the router. I plugged in both ends and removed the wireless dongle, but no joy... I thought it usually was the wireless thing causing issues... :confused:
Anyways, I connected other boxes using the same patch to see if there was some issue with my patching but they all work properly with this patch. I then booted into 7 and surprise, surprise, I do have a wired connection with the same patch.
The only thing I can think of is that the box was in standby while I switched to wired, but I thought that shouldn't matter as Ubuntu normally switches automatically to wired whenever a cable connection is detected.
What am I missing here? This really has got me baffled...

Ah, the system is Ubuntu Karmic...

---

### Post by warfacegod on 2010-04-28
Right click your Network icon to see if Networking is enabled.

---

### Post by Leppie on 2010-04-28
yeah, networking is enabled.
also, when i plug the wireless dongle back in it connects without any issues to the wifi network.

EDIT: the system doesn't seem to pick up the nic.

---

### Post by warfacegod on 2010-04-28
Check your Network Connections and make sure the wired connection is checked as Connect Automatically.

---

### Post by Leppie on 2010-04-28
For some reason the driver doesn't pick up my nick.
I've an identical system here which is working perfectly fine (did the same switch to wired connection, with the only difference that that machine wasn't in standby at the time).

EDIT: the crazy thing is that the wired connection doesn't work with the livecd either...

---

### Post by warfacegod on 2010-04-28
If it wasn't working in Windows, I'd say your Ethernet card is shot. Looks like you'll be looking for a driver for it. Although, I've never heard of needing find a driver for an Ethernet card.

---

### Post by Leppie on 2010-04-28
> **warfacegod said:**
> Looks like you'll be looking for a driver for it. Although, I've never heard of needing find a driver for an Ethernet card.
indeed, this card uses the Broadcom Tigon 3 kernel module (tg3)...
the other box is using it without any issues.
the part that puzzles me most is that it's not even working with the livecd (it worked when I installed Ubuntu initially on this machine).
not sure it's worth the effort spending more time on this since Lucid should be available very soon. With all the latest kernel modules I suppose it should work again ;)

---

### Post by warfacegod on 2010-04-28
If not then stare at it mean and threaten to replace it.

---

### Post by Leppie on 2010-04-28
> **warfacegod said:**
> If not then stare at it mean and threaten to replace it.
usually a light slap works for me... i'll try the staring ;)

---

### Post by P4man on 2010-04-28
My onboard network card (via rhine II) doesnt work after a resume from standby either, and its not even needing any proprietary drivers. Here is the (long standing) bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267779)

There are fixes in there that work fine for me, but note its a different fix for karmic and lucid.  

You will obviously have to replace via_rhine with the module used by your nic, but there is a fair chance it will solve it for you too.

For karmic and earlier:

> Create file /etc/pm/config.d/local with content:

SUSPEND_MODULES="via_rhine"

For Lucid:

> 1. create file /etc/pm/sleep.d/11ethernet

2. Put this into :

#!/bin/bash
case $1 in
    suspend)
        rmmod via_rhine
        ;;
    resume)
        modprobe via_rhine
        ;;
esac

3. save and make it executable chmod +x

---

### Post by Leppie on 2010-04-28
Thanks [P4man]("http://ubuntuforums.org/member.php?u=412374"), I'll give that a shot.

---

### Post by Leppie on 2010-04-29
i actually downloaded the Lucid rc, all is working fine now :)

---

