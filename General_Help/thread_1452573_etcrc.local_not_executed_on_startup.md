---
title: "etc/rc.local not executed on startup"
date: 2010-04-12
forum: General Help
---

### Post by MuffinMan123 on 2010-04-12
I usually set the transfer rate for wlan on start up because I dunno any other way of doing it. I find it weird that every other ubuntu versions can do rc.local at startup, even 9.10 xubuntu, but it didn't work for ubuntu.

how can I get the computer to run the script on startup? I tried to google for the problem but I only seen people mentioning the problem not the solution.

---

### Post by dcstar on 2010-04-13
> **MuffinMan123 said:**
> I usually set the transfer rate for wlan on start up because I dunno any other way of doing it. I find it weird that every other ubuntu versions can do rc.local at startup, even 9.10 xubuntu, but it didn't work for ubuntu.

how can I get the computer to run the script on startup? I tried to google for the problem but I only seen people mentioning the problem not the solution.

There is probably little point running a wlan script before the wlan is initialised and running.

Still using Network Manager, are you?

---

### Post by MuffinMan123 on 2010-04-15
I use wicd.
so you are telling me lan network is not set up yet when rc.local is executed? I thought re.local is done at the last step of the start up.

so when am I supposed to do ifconfig and iwconfig codes and how do I do it? I want to do it in start up so I don't have to do it by hand every single time

---

### Post by prodigy_ on 2010-04-15
IIRC, Network Manager starts working after a user has logged in. (Yeah, it's an abomination that needs to be put out of its misery.)

---

### Post by MuffinMan123 on 2010-04-15
if that's true, how come the same script works in 8.10?

---

### Post by Naggobot on 2010-04-15
See thread

[http://ubuntuforums.org/showthread.php?t=277997](http://ubuntuforums.org/showthread.php?t=277997)

Unfortunately this thread does not list how you can configure the script to run as last but man pages discuss the matter. I personally was unable to decipher the man pages when I was tinkering with this method so I had to stick with defaults. If you are able to configure your script to run as last item, please post command here. I need it too. 

To clarify, this method works in 9.10. If you can not find any way to run the script after network manager (if it is necessary to run the script after NM) then try sleep parameter in the script. I use the defaults and sleep 60 to login and continue the script after the login. I run a rsync script. 

Good luck with this if you try this.

---

### Post by prodigy_ on 2010-04-15
> **MuffinMan123 said:**
> if that's true, how come the same script works in 8.10?
Different configuration method, perhaps? You don't need Network Manager for WiFi to work. If your network adapter is configured via **/etc/network/interfaces** it'll be up by the time when **rc.local** is called.

---

### Post by MuffinMan123 on 2010-04-28
ok I am still not sure what's going on here.

network manager is the default UI that came with ubuntu 9.10 for network connection right? so if I uses wicd, it automatically replaces network manager when I installed it. I hope network manager is some command line stuff that I have never seen before.

so when does rc.local run? I remember there's a scripts that lists when each item is supposed to initiate, can I edit that file and put rc.local at the bottom?

someone gotta had it figured out by now...

---

### Post by LeeDaugherty on 2010-04-29
True, rc.local runs last in the sysv scripts (S99), but due to the new upstart, these scripts are becoming a thing of the past.  Instead of ordered running, upstart is event based.  In order to cheat a faster boot (kind of...but a valid cheat), NetworkManager is loaded after gdm.  rc.local should NOT be used for networking modifications.  /etc/network is the place for these. If you make yourself a bash script and place it in /etc/network/if-up.d if will run everytime Networkmanager (or any program really) toggles an interface up.  The script that runs all these can be found in /etc/NetworkManager/dispatcher.d ...and yes it used to work in previous editions, but no longer, but rc.local wasn't designed for networking mods, the /etc/network folder needs to be used for these as interfaces go up and down, and the scripts needs to be run every time that happens.
     When you make your script be advised that the scripts are run in alphabetical order (and make sure your permissions are right, it has to be owned by root and executable)...don't shoot me if this doesn't work, but it should put you in the right direction:
(name it zwifirate and save it in /etc/network/if-up.d) (what happend to using 25/75/numbers? geez!)

#! /bin/sh

IWCONFIG=/sbin/iwconfig
IF_WIRELESS_RATE=54M

#Description: Sets rate for wlan0 interface on start

#This assume wlan0 as the interface and is a really trashy way to write a script but works here
if [ "$IFACE" != wlan0 ]; then
      exit 0
fi

#Make sure this only runs when coming up
if [ "$MODE" != start ]; then
     exit 0
fi

#iwconfig commands
$IWCONFIG "$IFACE" rate $IF_WIRELESS_RATE

Again try saving that in /etc/network/if-up.d
Make sure it's root owned: 'sudo chown root:root /etc/network/if-up.d/zwifirate'
and executable: 'sudo chmod 0755 /etc/network/if-up.d/zwifirate'

Then just to make sure, reboot.  It's 430a, so I might have a typo in there, but let's hope that works.  It should set the rate everytime the wlan0 connection comes up. There is probably an easier way to do this, but this is the most proper way in my mind at 430a.--hope this works! and answers your question!

---

