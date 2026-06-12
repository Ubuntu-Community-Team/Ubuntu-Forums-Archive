---
title: "python program to load as a process during startup"
date: 2009-09-28
forum: General Help
---

### Post by pubsoftware on 2009-09-28
Hello,
 

 I am trying to get a python program to start during a reboot.  I am using ubuntu 8.04.
 

 Currently I have a simple script in my /usr/bin folder called 'startserver'
 

 contents:
     cd /home/pub/3/server/bin 
     exec /usr/bin/python ./server.py
 

 I also have a script in /etc/init.d based on the skeleton.  It has been registered for starting automatically with the command *update-rc.d * 
 

 The python program needs to be run as my default user 'pubuser' which of course has a password.  The python program also connects to a postgres database and does not seem to have the correct permissions to connect since the startup programs are run as 'root'.
 

 My questions are: Can the script start with the correct user as above?  How can I enable logging to see what is happening when the server boots and this process is loading?


I can see my program running since it has a process ID, but otherwise it is not working.

 

 Any other help appreciated.

---

