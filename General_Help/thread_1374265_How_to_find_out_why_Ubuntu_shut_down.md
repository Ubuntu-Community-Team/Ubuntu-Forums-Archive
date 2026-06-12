---
title: "How to find out why Ubuntu shut down"
date: 2010-01-06
forum: General Help
---

### Post by chrisbay90 on 2010-01-06
Hi,  I am running Ubuntu 9.10. I left it running over night to torrent (Ubuntu server 9.10 :) I can feel my home server getting closer every day). However I just woke up to find it off (fully shutdown not asleep or in hibernation)  How might I decern why ubuntu shutdown. I know in the past I have managed to find out myself but scavenging the logs. However i just cant seem to recall which log. If there is a better place to look than logs I'm all ears.

---

### Post by prem1er on 2010-01-06
Your best bet would be the logs (sorry to say), but they are there for exactly these sorts of reasons. There is a log viewer in Ubuntu that makes things much easier though.

System -> Administration -> Log File Viewer

Here is a good link that will explain what can be found where. 

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

I would start by looking in kern.log and messages for the timestamp of your last boot and work back from there. Post any output you find might be the problem.

---

### Post by bodhi.zazen on 2010-01-06
IMO the most likely explanation is hardware.

Is the server over heating ? Open the case and make sure it is clean inside and the fan vents are not obstructed.

#2 Would be power supply.

---

