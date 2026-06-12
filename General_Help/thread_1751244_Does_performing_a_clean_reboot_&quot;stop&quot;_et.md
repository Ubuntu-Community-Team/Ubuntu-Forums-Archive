---
title: "Does performing a clean reboot &quot;stop&quot; /etc/init.d scripts?"
date: 2011-05-06
forum: General Help
---

### Post by Amivit on 2011-05-06
Although I am not running Ubuntu (running Amazon Linux AMI on a free tier EC2 instance), I would like to know whether or not typing "reboot" at console implies that all scripts in init.d are cleanly "stopped". The reason I ask is that my little virtual server is used as a minecraft server, and issuing /etc/init.d/minecraft stop automatically stops the minecraft server cleanly and saves the world. 

But I noticed when I reboot the server and check the minecraft log, the server seems as if it is just "killed" which can corrupt the world :/. How do I ensure **/etc/init.d/minecraft stop** is executed apon server shutdown/reboot?

---

