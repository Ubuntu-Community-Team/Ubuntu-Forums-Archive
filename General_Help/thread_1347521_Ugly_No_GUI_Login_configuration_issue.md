---
title: "Ugly No GUI Login configuration issue"
date: 2009-12-06
forum: General Help
---

### Post by Reston Marcus on 2009-12-06
Good day all,
 

 Need assistance to become aware on how to repair login to the GUI. Since 8.04 I have upgraded (traded -- v-e-r-y hard time consuming task) laptops and such, to be able to simply run Ubuntu so that I could be able to learn this OS. I'd really like this OS to permanently replace MS-Windows (I'm a linux noob w/little info and familiarity).
 

 Well, now I have an ultra loaded, touch-screen capable, Lenovo t400 laptop with fingerprint activation capability loaded initially with Win-XP.
 

 I upgraded and removed XP for Win-7 Ultimate. After modifying and tweaking it to the max, I decided to try Ubuntu 9.10 after much review and study (today I found this thread).
 

 After that successful install and then the inclusion of some fancy stuff like Compiz, Awn, box, then 3d translucent circle etc. (which is PHAT) and maintaining automatic log-in for rebooting, suddenly I could not get to the GUI but only to a flickering command-line.
 

 After review and soliciting aid from the community, I did get a single suggestion to try:
 

 “ sudo /etc/init.d/gdm start”
 

 The response to this was:
 

 “since the script you are attempting to invoke has converted to an upstart job, you may also use the “start 8 utility,” e.g. “start gdm start/running, process 2181.”
 

 after trying “start gdm start/running,” I got the message, “no seat id found.”
 

 Then out of curiosity, I tried, “gdm gdm/start” and got this message:
 

 “Failed to acquire org.gnome.DisplayManager Connection “1:20” is not allowed to own the service due to security policies in configuration file.”
 

 Please aid me to repair this so that I can get on my personal mission to assist others too. Don't have a clue on how to adjust the configuration file and scared to blindly attempt all that I've found in Chimmer's thread (# 8393913) but I will, if prodded.

---

