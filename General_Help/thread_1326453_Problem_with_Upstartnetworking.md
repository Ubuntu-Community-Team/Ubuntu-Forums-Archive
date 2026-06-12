---
title: "Problem with Upstart/networking"
date: 2009-11-14
forum: General Help
---

### Post by kylegio on 2009-11-14
i am posting this thread as a spin-off of a previous thread about networking trouble, i have narrowed the problem down to upstart and think that i would get more help with a thread whose topic reflects the problem. 
link to previous thread, please if you are interested in this issue check out this thread near the end where i start to narrow down the cause:
[http://ubuntuforums.org/showthread.php?p=8315381](http://ubuntuforums.org/showthread.php?p=8315381)

initially the problem occured after a 9.04(serveR)->9.10(server) upgrade, the problem is that networking does not properly start upon bootup, an ifconfig after boot returns nothing (not even loopback)

then using /etc/init.d/networking restart i could get the networking to start properly
also using ifup -a works perfectly (this is important because the /etc/init/networking.conf and network-interface.conf files use this to setup interfaces (it appears)

the problem has been narrowed down to an upstart issue, the init.d file for networking clearly shows how it starts networking
```
start)
      /lib/init/upstart-job networking start
      ;;

stop)...etc
```

initially invoking that command returned an unknown job error and networking would not start, i then determined that i was missing the /etc/init/networking.conf and network-interfaces.conf files, i copied them from my desktop (9.10desktop) and the command seemed to work. 

before replacing these files the "initctl list" command did not list anything containing the word "network" at all, after replacing these files the "initctl list" command shows
```

...
network-interface start/running (it does not give a device name)
networking stop/waiting 
...
```

comparing to my desktop my desktop has a network-interface **ADAPTOR NAME** start/running for each adaptor  for example 
"network-interface eth0 start/running"  and does them all. 

my server does not. 



this morning after sleeping on the problem i rebooted my server and tried again, the /lib/init/upstart-job networking start only to get a "job failed to start" error, this is the same with "sudo service networking start", and of course /etc/init.d/networking start as it calls on upstart-job 


does anyone have suggestions?, furthermore does upstart log any errors/status messages? im looking through log files and can find nothing relating to networkings inability to start.
best i could find in the daemon.log file "networking main process terminated with status 1"

---

