---
title: "Python scripts are not ran by rc.local at startup."
date: 2011-11-22
forum: General Help
---

### Post by corina_pelmus on 2011-11-22
Hello, 

I am running an Ubuntu 8.10 2.6.27-11-generic i686. I have 2 python scripts which I want to run at startup from rc.local.

They are ran as: /etc/init.d/script_x.sh start, script_x.sh being 2 custom shell scripts that start/stop/restart these services.

For some reason, these two particular scripts are not ran in rc.local. They are ran if I run:

sh -Vx /etc/rc.local
or
/etc/init.d/script_x.sh start

but not if I run 

/etc/rc.local

I suspect a shell issue, but I am just not able to see it.

The shell script from rc.local is written in shell :
#!/bin/sh.

Please advise :)

Corina

---

