---
title: "Really strange happenings"
date: 2006-03-26
forum: General Help
---

### Post by barfos on 2006-03-26
I don't know if this stuff is related or not...

This all started after I did automatic update and got new linux kernel.  It told me to reboot, but I didn't... not immediately.  Don't know if this is the cause.

First certain dialogs will take near infinite time (several minutes) to open.  This includes the folder sharing dialog in nautilus, the list of shares in the system>administration menu, and the network configuration thing.

Second, when shutting down or rebooting the machine, it will hang on Stopping portmap daemon...  for several minutes before continuing.

Another thing is the automatic network configuration on boot.  It doesn't work anymore.  I looked around for a solution to that, and checked the /etc/network/interfaces file for clues.  This is what I get...

```


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp



iface wlan0 inet dhcp
wireless-essid rpgbreakfast
wireless-key 2C5310534AA1C7A7EFAC73B3E7
schedule for immediate present
school things to do
hobby projects
lerna&#309;oj ke mi neniam povos fari
songs to look for
machines specs
WEP key here
schedule for immediate present
school things to do
hobby projects
lerna&#309;oj ke mi neniam povos fari
songs to look for
machines specs
WEP key here













auto eth0



```

You are wondering what all that crap is near the end.  I am as surprised as you.  It's a list from one of my tomboy pages, a desktop reminder-notes applet.  How did that text get from a note into a system configuration file owned by root?  Obviously I need to remove it from the file...  but huh????


None of this makes sense!  Let's hope I'm some huge idiot, because if this kind of crazy stuff starts happening in ubuntu on a regular basis (to other people), we got problems.

barfos

---

### Post by Ramses de Norre on 2006-03-26
Is the problem solved by deleting all the lines beneath "wireless-key 2C5310534AA1C7A7EFAC73B3E7" ?

I have really no idea how it gets there.. It's indeed very weird.

---

### Post by barfos on 2006-03-26
I fixed all those problems.  I wish i understood the situation more but....

So I noticed I couldn't type
ping 127.0.0.1
ping localhost
ping 192.168.0.24 (my ip address)

it would just hang.  I checked the routing table with the route command and saw no route for the localhost.  I did this

sudo route add localhost dev lo

and everything worked.  My samba shares were working (accessible), the dialogs all took 1 seconds to pop up, the portmap thing will probably work, though i removed the nfs packages.  The only question is how to make all this work the way it should next time i reboot.  Time for the interfaces man page.

---

