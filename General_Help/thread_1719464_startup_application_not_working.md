---
title: "startup application not working"
date: 2011-04-01
forum: General Help
---

### Post by ark on 2011-04-01
Good day,

I have a problem with my media center, specifically with an App that is called downpour, it is a Bittorrent client. I cant get it to start at startup. when i installed it it was working but some days ago i did an update on ubuntu and it stop loading at startup.
(it's listed on the system > preferences > startup applications)

This is what i have tried already...
I read that it could be because ubuntu start at filesafe but it is not. 

xbmc loads at startup

installed and added to system > Preferences >startup applications  another bittorent client (qtorrent) and it loads. 

added the command to /etc/rc.local file

checked and unchecked the app on the list of startup app

checked the Automatically remember running applications when logging out

restarted the PC a million times

the command works anytime on console

by the way the command is
sudo downpourd -c /etc/downpour.cfg

I added the user so that it doesn't require a password to use sudo

The command was working as it is before the update.



any help is appreciated
regards

---

### Post by ark on 2011-04-07
any ideas and/or alternative ways to start the daemon at boot time?

---

### Post by TeoBigusGeekus on 2011-04-07
Just an idea...
```
sleep 10 && sudo downpourd -c /etc/downpour.cfg
```

---

