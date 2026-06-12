---
title: "CSS server hosting help"
date: 2010-12-01
forum: General Help
---

### Post by renegadeandy on 2010-12-01
Hey guys, I installed a CSS server following these instructions on the latest Ubuntu server :

[http://ubuntuforums.org/showthread.php?t=76483](http://ubuntuforums.org/showthread.php?t=76483)

And I then created + configured my server as per the bottom of this suggesting the server config creator tool :

[http://counterstrikesource.mediasmok...opic.php?id=29](http://counterstrikesource.mediasmok...opic.php?id=29)

All fine - then i go to run my server by doing :


sudo ./srcds_run -console -game cstrike +map de_dust

and it says:

Code:
andy@novo:~/srcds/orangebox$ sudo ./srcds_run -console -game cstrike +map de_dus
t
Auto detecting CPU
Using default binary: ./srcds_linux
Server will auto-restart if there is a crash.
Illegal instruction
Add "-debug" to the ./srcds_run command line to generate a debug.log to help with solving this problem
Wed Dec  1 16:22:40 GMT 2010: Server restart in 10 seconds
Illegal instruction
Add "-debug" to the ./srcds_run command line to generate a debug.log to help with solving this problem
Wed Dec  1 16:22:50 GMT 2010: Server restart in 10 seconds
Illegal instruction
Add "-debug" to the ./srcds_run command line to generate a debug.log to help with solving this problem
Wed Dec  1 16:23:00 GMT 2010: Server restart in 10 seconds
^X^CWed Dec  1 16:23:01 GMT 2010: Server Quit
In a never ending loop - i then add the -debug flag - and do sudo updatedb then locate debug.log but none has been created...

Please help,

Andy

---

### Post by renegadeandy on 2010-12-01
Any ideas!?

---

### Post by renegadeandy on 2010-12-01
Debug log has now been produced :

[http://pastebin.com/iTwLnXW2](http://pastebin.com/iTwLnXW2)

---

