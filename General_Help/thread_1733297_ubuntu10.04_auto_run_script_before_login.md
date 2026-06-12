---
title: "ubuntu10.04: auto run script before login"
date: 2011-04-19
forum: General Help
---

### Post by richard_wu0313 on 2011-04-19
hi forks,
i have a script need to auto run before login. i have tried to add it in /etc/rc.local and using update-rc.d, both failed. any help would be appreciated.

[COLOR="teal"]/etc/rc.local[/COLOR]
has update link from dash to bash
#! /bin/sh
sleep 5
/etc/init.d/do_script.sh
exit 0

[COLOR="Teal"]update-rc.d do_script.sh defaults 95[/COLOR]

---

### Post by djsg on 2011-06-27
Hi Richard,

have u solved ur problem?

I have similar problem here. I want to use myscript.sh to auto-start an application. I put myscript.sh into /etc/init.d/ and run *update-rc.d myscript.sh defaults*. I can see my application was started (its log file was updated), but I cannot see my application running if I do *ps -ef*. I suspect it is killed by the OS. 

Can someone help?

---

### Post by furtypajohn on 2011-06-29
Richard: Did you try putting it in /etc/init.d? 
See: [http://ubuntuforums.org/showthread.php?t=345614](http://ubuntuforums.org/showthread.php?t=345614)

djsg: I suspect that since the script is actually being run you did the setup properly, but there is probably an error in your script that is causing it to terminate.

---

