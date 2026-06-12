---
title: "tsclient autoconnect?"
date: 2011-05-10
forum: General Help
---

### Post by remymf on 2011-05-10
:guitar:Hello, i am fairly new to linux and i am trying to figure out a way to automatically connect with tsclient to a windows computer at startup. I have tested, and i connect fine with tsclient. I then wrote a script that looks something like this 
 
#!/bin/bash
 
tsclient -x /location/of/my.rdp 
 
after i made this i did 
 
sudo chmod 777 -x /location/of/bash 
 
then i put the /location/of/my.rdp into the startup applications under
System > preferences > startup applications
 
:popcorn:This works sometimes, and it will startup in a windows login screen. However after a few seconds it will jump back to the ubuntu background. I would like to figure out how i can make this script run in a loop of some sort that will check to see if tsclient is running and connected. if it is connected it will do nothing, but if it is not connected it will run that
 
tsclient -x /location/of/my.rdp file 
 
:mad:Although this seems simple, i can not find anything on the subject, that answers the question simply. The closest thing i have found was code that used a 
 
while true; do tsclient -x my.rdp; sleep 5s; done
 
but from what i read it ran tsclient every 5 seconds regardless. i would like the user to never see ubuntu if at all possible. If you can give me any advice, i would much appreciate it. I am using Ubuntu 10.04.2 to connect to a windows xp computer. :confused:

---

