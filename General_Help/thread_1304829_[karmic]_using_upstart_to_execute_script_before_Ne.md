---
title: "[karmic] using upstart to execute script before NetworkManager starts?"
date: 2009-10-29
forum: General Help
---

### Post by kayzu on 2009-10-29
hi, on 9.04 i just had a line in rc.local saying "ifconfig wlan0 hw ether ..." to change the MAC address on every boot. This command has to be executed before the NetworkManager starts because it acts up otherwise.
Now what would be the best way to achieve this on karmic? adding it to rc.local doesn't work anymore because networkmanager is already started at that point. i've never dealt with upstart before. so i have to somehow get that ifconfig command to execute before the networkmanager starts, can anyone help?
thanks :)

---

### Post by kayzu on 2009-10-31
bump.. does anyone know how to do this?

---

### Post by lotuseclat79 on 2009-11-03
Hi kayzu,

I'm going to hazard a guess at this that if you insert what you need just before the upstart in the start) case of /etc/init.d/networking - you might be successful.  Be sure you save the original file which a different suffix like .orig if it does not work so you can easily restore it.

/etc/rc0.d/S35networking is a symbolic link to /etc/init.d/hetworking where the sequence of commands I am talking about is line 51-55:
case "$1" in
start)
        /lib/init/upstart-job networking start
        ;;

So, in other words, you would wind up with something like:
case "$1" in
start)
        ifconfig wlan0 hw ether ...
        /lib/init/upstart-job networking start
        ;;

Just a SWAG on my part, and no guarantee it will work, but I think it is worth a try.  Note: I am assuming networking starts before the NetworkManager process, and in that case, you could even try putting your ifconfig statement just after the upstart statement, however, I do not know if the upstart of networking also results in starting up the NetworkManager process at that point in the boot up deeper in the code somewhere.

-- Tom

---

### Post by Despot on 2009-11-10
lotusclat's solution might work, but there's a better way...

In Karmic, the Network Manager is started from Upstart, which keeps its init files in "/etc/init" You'll want to edit the network-manager.conf file in this directory, which is responsible for starting Network Manager. To execute a script before Network Manager starts, add a stanza like this:

```
pre-start script
     ifconfig wlan0 hw ether ...
end script

```

Then restart. More information on Upstart is available at upstart.ubuntu.com, and you can also look at the existing scripts for examples.

---

### Post by kayzu on 2009-11-10
hi, thanks for the replies but i noticed that a simple "ifconfig hw ether <mac>" doesn't work as i expected when run as prestart to the network-manager.

obviously, i'd have to take the interface down beforehand and start it again after changing the mac. i guess i could do that in there aswell, but is there a better place to put it to be executed right before the interface is coming up?

in jaunty all i had to do was put the one line to change the mac in the rc.local and it worked, but apparently that doesn't work on karmic anymore, looks like the rc.local is executed after some of the init scripts and the interface/network-manager is already up..

---

### Post by Despot on 2009-11-11
Problems with things not behaving correctly in Upstart have usually been typos or such for me. I would start by making sure to use the full path to ifconfig (this is generally good practice in scripting anyway), and also redirecting output to temporary files like so:

```

pre-start script
     /sbin/ifconfig [options] 1>/tmp/debug.log 2>/tmp/debug_error.log
end script

```

This should give you a good idea of what's causing your script to fail. Issuing the "initctl log-priority debug" command, then running your script manually and checking /var/log/daemon.log can also be useful.

---

