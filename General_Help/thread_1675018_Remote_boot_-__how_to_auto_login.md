---
title: "Remote boot -  how to auto login?"
date: 2011-01-24
forum: General Help
---

### Post by bbain on 2011-01-24
I am admittedly a noobie, trying to help my son out while he's away. The server is a HP Proliant DL140, with Ubuntu 10.10.  I would like to be able to use WOL to start up a server, then have it automatically login into a user account so that the remote user can use VNC.  I can get the server started using WOL, but I haven't been able to figure out how to automate the login so that VNC will run.  That way he can run his MySQL queries, webmin administer the server, etc. remotely.

There may be better way to do this and I'm open to suggestions.  For him to access the server and have WOL work, I've had to place it outside the router firewall in a DMZ, so we'd prefer not to leave it up all the time if we can avoid it.   Thanks in advance.

Bill

---

### Post by bbain on 2011-01-27
** bump **

> **bbain said:**
> i am admittedly a noobie, trying to help my son out while he's away. The server is a hp proliant dl140, with ubuntu 10.10.  I would like to be able to use wol to start up a server, then have it automatically login into a user account so that the remote user can use vnc.  I can get the server started using wol, but i haven't been able to figure out how to automate the login so that vnc will run.  That way he can run his mysql queries, webmin administer the server, etc. Remotely.

There may be better way to do this and i'm open to suggestions.  For him to access the server and have wol work, i've had to place it outside the router firewall in a dmz, so we'd prefer not to leave it up all the time if we can avoid it.   Thanks in advance.

Bill

---

### Post by Krytarik on 2011-01-27
How about "System -> Administration -> Login Screen", "Log in as USERNAME automatically"?

More info regarding GDM here:
[http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig](http://library.gnome.org/admin/gdm/stable/configuration.html.en#daemonconfig)

---

### Post by bbain on 2011-01-28
Thank you.  I will give that a try.

---

### Post by bbain on 2011-01-30
Well. it almost works the way we'd like.  It logs hom in but throws up a confirm screen that has to be clicked through.  Net result is that the VNC server doesn't launch until *after* the login, which doesn't help since without VNC running, he can't click through the confirm.

I've heard of "lights out" data centers and "headless" servers whch would seem to have eh same some of problem if a server needed to be rebooted.  I must be missing something in the setup.  Thanks for everyone's help in advance.

Bill

---

### Post by Krytarik on 2011-01-30
How do you set up the remote connection?

See this thread about a similar topic:
[http://ubuntuforums.org/showthread.php?t=1676084&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=1676084&highlight=x11vnc)

---

### Post by tredegar on 2011-01-31
> Well. it almost works the way we'd like.
I start a vnc server on my server when it boots, with this in **/etc/rc.local**

```
# Start a vnc server for the user install
su - install -c "cd /home/install && vncserver -geometry 1024x768 -depth 24 :1"
```

I connect to it with **vncviewer server:1**

My server is on my LAN and behind a firewall. Exposing vnc to the internet is a security risk.

---

