---
title: "How to auto-start GUI app using upstart"
date: 2012-08-15
forum: General Help
---

### Post by ConanTheNewb on 2012-08-15
**Goal:**
Use upstart to launch a GUI app.
(while I do understand that I can use unity gear menu's "start applications" option to launch a GUI app, I'd like to understand how to launch a GUI app from upstart)

**Using:**
Ubuntu 11.10
upstart
unity
 
**What works:**
Let system boot up
open a terminal
xclock -update 1
(clock displays and operates normally)
 
**What also works:**
I've written a number of /etc/init/xxx.conf files starting up non-GUI apps during bootup, so I'm an advanced beginner with upstart. But no expert.
 
**What does not work:**
I have this my.conf file:
 
[FONT=Courier New]start on desktop-session-start[/FONT]
[FONT=Courier New]stop on [!2345][/FONT]
 
[FONT=Courier New]env DISPLAY=:0.0[/FONT]
 
[FONT=Courier New]script[/FONT]
[FONT=Courier New]echo "hello" >> /tmp/upstart.log[/FONT]
[FONT=Courier New]exec xclock -update 1[/FONT]
[FONT=Courier New]end script[/FONT]
 
**How does it fail:**
1: the "hello" is proper logged to the upstart log so I know that it is getting the event.
2: dmesg reports that the xclock process exited with code 1
3: no clock appears
4: aside from that, system boots and prompts for log on normally
 
**What am I doing wrong?**
[FONT=Tahoma]1: is desktop-session-start too early for a GUI app to start?[/FONT]
[FONT=Tahoma]2: do I need to provide some permission (xhost?) to allow a GUI app to start?[/FONT]
[FONT=Tahoma]3: other?[/FONT]

---

