---
title: "Ubuntu server just dies. Why?"
date: 2011-07-04
forum: General Help
---

### Post by megabuffen on 2011-07-04
I have two servers, both running Ubuntu 11.04 Server. One is a web server, running only a LAMP stack and openssh-server. The other is running server daemons for TeamSpeak and Minecraft. Today, the game server just went down. I can access the LAN by using SSH to connect to the web server, and ping it from there. However, it won't respond to SSH or anything else. The server is a few kilometers from here, so I will be going there tomorrow.

This happened once before, probably about a month ago or something. That time, the web server was running just fine, but the game server was powered off. I thought there had been a power disruption, because when I checked the BIOS settings of the game server, it wasn't set to resume after AC power loss. The web server was set to do this, so it made sense that it would be up and running again after a brief power loss. There were also some news reports about power disruptions in my area.

The thing is, I changed the BIOS settings of the game server to make sure this wouldn't happen again. When I go there tomorrow, I will bring the server back up. However, I would like to know what caused this so that I may prevent it from occurring again. Is there a logfile or something that I can check tomorrow to find the problem?

---

### Post by dcstar on 2011-07-05
> **megabuffen said:**
> 
..........
This happened once before, probably about a month ago or something. That time, the web server was running just fine, but the game server was powered off. I thought there had been a power disruption, because when I checked the BIOS settings of the game server, it wasn't set to resume after AC power loss. The web server was set to do this, so it made sense that it would be up and running again after a brief power loss. There were also some news reports about power disruptions in my area.
.........

Any power loss can corrupt a system past the point of being able to reboot (as well as destroying data), that is why things like UPS exist.

You are just lucky that your other system came up after a power outage.

---

### Post by dandnsmith on 2011-07-05
There may be lots of logs in /var/log, but the usual situation is that the system dies before anything can get logged, and when it comes up again the conditions have changed.

---

