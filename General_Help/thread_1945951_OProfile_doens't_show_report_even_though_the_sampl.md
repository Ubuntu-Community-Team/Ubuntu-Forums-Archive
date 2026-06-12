---
title: "OProfile doens't show report even though the sample file exist"
date: 2012-03-23
forum: General Help
---

### Post by wlouis on 2012-03-23
I am having difficulties letting OProfile to run. The thing is it seems to be running but doesn't show me the report. When I run opreport, it gives the following error: OPreport error: no sample file found. Try running --dump or specify a session containing sample files. 
 
If I do the following steps 'exactly'
 
# opcontrol --no-vmlinux
# opcontrol --start
Profiler running.
# ~/hello-2.1.1/src/hello
Hello, world!
# opcontrol --stop
Stopping profiling.
# opcontrol --dump
 
then run opreport I get the error above.
If I go to /var/lib/Oprofile/Samples, I see a file called OProfiled.log ... If i check the date this file is updated, it shows the exact time that I did opcontrol --dump ! Doesn't that mean it is working properly ?
 
I tried opreport --session-dir= ( the oprofiled.log file place), and wasn't successful.
 
The only steps I did for OProfile install was apt-get OProfile then run the code above. Is there anything else I need to add ? am I missing anything ? Do I have to specify some event so OProfile works correctly ?
 
My Oprofile version is 0.95cvs and ubuntu 9.4 
 
Please advise,

---

### Post by wlouis on 2012-03-24
Any input is appreciated .
 
Thanks

---

