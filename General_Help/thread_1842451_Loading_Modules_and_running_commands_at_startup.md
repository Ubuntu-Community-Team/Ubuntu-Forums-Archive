---
title: "Loading Modules and running commands at startup"
date: 2011-09-11
forum: General Help
---

### Post by ligiopro on 2011-09-11
I'm trying to use a program called k10ctl on 10.04.
Right now, once I'm on the desktop, I have to run the following commands to use it:

sudo modprobe msr
(the following modifies default settings)
sudo k10ctl 0-3 1 -cv 30 -cf 6
sudo k10ctl 0-3 2 -cv 38 -cf 0

I want to automate this process and have them run before I log on. 

To load msr, do I just type msr into the file: /etc/modules.conf?

However, I'm not sure how to execute the k10ctl commands at startup (with root privileges so I don't have to type my password).

---

### Post by wt8008 on 2011-09-12
The file I see shows /etc/modules without the .conf

Maybe you need to create a system service that will run those two commands at boot.

---

### Post by brucehohl on 2011-09-12
If you put those commands in /etc/rc.local such that the file will look like below they will be run at start-up:

root@HP-3500:/etc# cat rc.local
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

modprobe msr
k10ctl 0-3 1 -cv 30 -cf 6
k10ctl 0-3 2 -cv 38 -cf 0

exit 0

---

