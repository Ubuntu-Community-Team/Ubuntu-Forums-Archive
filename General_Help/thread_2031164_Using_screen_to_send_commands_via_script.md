---
title: "Using screen to send commands via script"
date: 2012-07-21
forum: General Help
---

### Post by sneak310 on 2012-07-21
Hey, I've been browsing several forums trying to figure out how to make this work but can't seem to find the answer. I'm running Ubuntu 12.04-LTS x64.

I have 7 Wolfenstein: Enemy Territory servers running and I'd like to properly shut them down by use of script. My method of starting each server is as follows:

```
screen -dmS probox ./etded.x86 +set fs_homepath "/home/probox/" +set fs_basepath "/home/probox/" +set net_ip 66.151.244.191 +set net_port 27970 +set sv_maxclients 18 +set com_hunkmegs 192 +set fs_game "etpro" +set dedicated 2 +exec server.cfg
```

So I guess I would need something which can enter screen for each screen identifier and execute the command "quit". My overall goal here is to make a script that will properly shut down all of my servers at once.

Thankyou.

---

### Post by sneak310 on 2012-07-24
bump

---

