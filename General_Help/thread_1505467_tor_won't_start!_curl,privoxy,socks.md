---
title: "tor won't start! curl,privoxy,socks"
date: 2010-06-09
forum: General Help
---

### Post by maratonic on 2010-06-09
Hi all, 
yesterday I set up tor and privoxy and used curl to send hthp requests through it. It worked fine. Today tor has stopped working and I need Your help, sir, to get it runnin again. 


My curl command and the following error are:

```
fred:~$ curl --socks5 http://127.0.0.1:9050 http://213.180.89.177
curl: (7) couldn't connect to host
```

If I don't try to route the request through privoxy/tor it works, i.e. if the request is simply 

```
fred:~$ curl http://213.180.89.177
```

Investigating this I seem to have a problem with tor not starting:
--------------
```
fred:~$ sudo /etc/init.d/tor start
 * Starting tor daemon (tor)... Jun 09 12:01:01.969 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jun 09 12:01:01.970 [notice] Initialized libevent version 1.1a using method epoll
                                                                                                                      [ ok ]
fred:~$ sudo /etc/init.d/tor restart
 * Stopping tor daemon (tor)...                                                                                       [fail]
fred:~$ sudo /etc/init.d/tor start
 * Starting tor daemon (tor)... Jun 09 12:06:13.678 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Jun 09 12:06:13.679 [notice] Initialized libevent version 1.1a using method epoll
                                                                                                                      [ ok ]
fred:~$ ps aux | grep -i tor
108       4353  0.0  0.0   2024   836 ?        S    09:15   0:03 /usr/lib/hal/hald-addon-storage
fred        6458  0.0  0.3   8520  3760 ?        Sl   11:16   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=31
fred        6484  0.0  0.9  66004 10292 ?        Sl   11:16   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=35
fred        6495  0.0  1.0  23080 10400 ?        S    11:16   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=37
root      6555  0.4  2.4  65992 25760 pts/0    Sl+  11:17   0:12 gedit tor_aliases
root      6570  0.0  0.3   8520  3760 ?        Sl   11:21   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=29
fred        6937  0.0  0.0   2876   792 pts/1    R+   12:06   0:00 grep -i tor
fred:~$
fred:~$ netstat -a | grep 9050
fred:~$ 
fred:~$ netstat -a | grep 8118
tcp        0      0 localhost.localdom:8118 *:*                     LISTEN

```
------------

Yesterday netstat -a | grep 9050 showed "tcp 0 0 localhost:9050 *:* LISTEN" ,as specified in the install instructions at [http://help.ubuntu.com/community/Tor](http://help.ubuntu.com/community/Tor)

My conclusion: tor says it is starting but it's not. 

How can I get it to run? I've tried updating tor with "apt-get install tor" but it says tor is already up to date. Triple-checked torrc, privoxy/config and tsocks.conf. Restarted privoxy and apache2 and tried to start/restart tor. Logged out and logged in again, rebooted the machine. Nothing helps. It's probably something silly but I can't find it.

Thankful for any advice.

  /Fred

---

### Post by maratonic on 2010-06-09
.

---

### Post by maratonic on 2010-06-10
Update: I have upgraded to the latest version of tor, I found a post saying the tor package is not maintained in the "ubuntu universe" and therefore apt-get had installed an older version. I added the correct path (as stated in the torproject.org faq) to /etc/apt/sources.list so now I have tor 0.2.

It still didn't work though, I got error an message indicating that tor during startup tried to open port 9050 twice and then shut down.

Then I removed tor and privoxy and renamed the config files: 

```

sudo apt-get remove tor privoxy
cd /etc
sudo mv tor/torrc tor/torrc.old
sudo mv privoxy/config privoxy/config.old

```

Installed both again and violá! Works again!
:guitar:

Sometimes the simple solution really IS the solution.

Hopefully this post may be useful to some other junior "ubunthusiast" just like myself.

  /Fred

---

