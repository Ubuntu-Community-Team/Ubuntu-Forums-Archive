---
title: "Help me stop a daemon !!"
date: 2009-08-15
forum: General Help
---

### Post by Cygoku on 2009-08-15
There is a daemon for pulse audio that loads on startup of my laptop.  Wich locks any application from using alsa.  If I kill the process using the System Monitor all apps have their sound working again.  

I.E. : I cannot watch youtube videos with sound unless I kill the pulse audio daemon.  

Please help preveting it's loading at startup !! 

Thanks in advance folks, 

Cygoku

---

### Post by ubudog on 2009-08-15
Open a terminal and type ```
cat /etc/rc.local
```  Post what you see. :)

---

### Post by Yellow Pasque on 2009-08-15
System -> Preferences -> Startup Applications

Ideally, you would want to fix the issue with PulseAudio instead of killing it. In GNOME 2.27/2.28 (which will be in Ubuntu 9.10), simple things like volume control and sound settings won't work without PulseAudio (a real pain for those running accessibility software, OSS4, or who just dislike PulseAudio).

---

### Post by Cygoku on 2009-08-15
> **ubudog said:**
> Open a terminal and type ```
cat /etc/rc.local
```  Post what you see. :)cygoku@shizzled:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
cygoku@shizzled:~$ 

... Cygoku

---

### Post by ubudog on 2009-08-15
If you know the name of the process, you can edit /etc/rc.local and make it run "killall processname" on startup.  :)

---

