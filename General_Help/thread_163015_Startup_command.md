---
title: "Startup command"
date: 2006-04-20
forum: General Help
---

### Post by ubernoob on 2006-04-20
How can i add a command after the boot and preferable before x-server starts?

---

### Post by dg_w on 2006-04-20
This depends, what is it you want to start ?
A script, a module to be loaded, for all users ?

If you can be more specific I will try to help :)

---

### Post by trent dillman on 2006-04-20
Make a script in /etc/init.d that starts/stops/restarts your custom stuff, then symlink to /etc/rc?.d/, where ? is the runlevel you want it to run at. Look around in those folders for examples. Also, the name of your symlink (I think) needs to conform to the rest (starts with K for kill, S for start; ## for run order; name of script).

---

### Post by ubernoob on 2006-04-20
sorry for not beeing clear. I just meant one simple command:
sudo hdparm -Y /dev/hda

---

### Post by dg_w on 2006-04-20
I have the SO7hdparm script in my /etc/rcs.d 
(so starts before the rest of the run level scripts)

Incidently, the Automatix installer script can set that up and put in pace for you :) 

Let me know I can paste the contents of the file for you..

---

### Post by ubernoob on 2006-04-20
I'm using dapper, so i don't think there is a compatible automatrix yet.

I would like to see how you have done it. Can you paste the file here?

I guess rc0 - rc6 is the diffrent runlevels. So "s" must be startup?

/etc/rcS.d/README says:
After the S40 scripts have executed, all local file systems are mounted

my /dev/hda is my /boot partiton. So i guess i should use S41 instead of S07? Or have i misunderstood?

---

### Post by dg_w on 2006-04-20
Yep I think the scripts in here run before the run level scripts, so a good place to put it. S"THEN NUMBER" relates to the order in which the script will run, 
SO7hdparm on my system, so create a script with a number following on from the last script in the /etc/rcs.d directory. (and make it excituable)

Heres my script..

Once you have set yours up try running in from the command line:

---

### Post by ubernoob on 2006-04-20
That file is identical with /etc/init.d/hdparm and doesn't give me any more understanding at all. Do you mind explaining what you did with it and for what purpose?

I made a simple bash command:
```
#!/bin/bash
hdparm -Y /dev/hda
```

and made it S41. It seems to work like i wanted it to. But when i logged into gnome, my harddisk started up again...

---

### Post by trent dillman on 2006-04-21
The scripts in /etc/rc?.d/ are generally symlinks to /etc/init.d, and I believe the first letter (S,K) issues a start/stop command to the script.

In my /etc/init.d/hdaprm, there's a note:

```
#In certian cases you may wish to run this script twice.  Once at S07
#and once later in the boot process. If you do this call /etc/init.d/hdparm
#again from rcS.d with a name such as S27hdparm.second.
#
#See /usr/share/doc/hdparm/README.Debian for more details.
```

---

