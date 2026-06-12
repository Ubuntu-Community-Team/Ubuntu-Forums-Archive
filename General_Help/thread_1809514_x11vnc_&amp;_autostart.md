---
title: "x11vnc &amp; autostart"
date: 2011-07-21
forum: General Help
---

### Post by KillerLink on 2011-07-21
Hi to Forum!
Im New, my name is Theodor and im from Austria, 
so please forgive me, if my englisch is bad. 
In that case, please give me a second try to explain what i meant.

Information:
Running OS: 11.04 ubuntu desktop

At first i wanted to use the built in method of ubuntu to share it's screen. It's also a kind of vnc server if i got that correctly. i was able to connect with a vnc viewer, problem was: the picture the vnc viewer showed me didn't refresh. i could reconnect to refresh, but this is not efficient ; )
So I searched the web for a solution, i found out that it is recommended to use another vnc client called x11vnc. i installed it and was able to connect, picture refreshes correctly, fine ; )
Next Step: The Computer running the vnc server will run without a monitor i future, so only way to see what the computer does, is connecting a vnc viewer. since the pc even starts without monitor or keyboard, i want it to start x11vnc automatically. 
so i set up auto-login and created a new auto-startup entry containing the command:
x11vnc -usepw
this works fine i thought, since i found out i can connect only once, until the next reboot.
i found 2 working solutions how to alter the startup command:
1) --> x11vnc -usepw -forever
2) --> x11vnc -usepw -loop
both of those seem to work as i want it. :)

But now i want to now what exactly i was doing XD
My 3 Questions are:
1) Is there no solution for the first problem it wrote (the not refreshing screen)  except using x11vnc server? I would appreciate it to use the buil-in method in ubuntu.
2) what excatly happens if i add -forever to the (or any other) command?
2) what excatly happens if i add -loop to the (or any other) command?

with best regards
Theodor alias KillerLink

---

