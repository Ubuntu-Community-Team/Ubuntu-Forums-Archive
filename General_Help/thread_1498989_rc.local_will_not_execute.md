---
title: "rc.local will not execute"
date: 2010-06-01
forum: General Help
---

### Post by pauldemet on 2010-06-01
I have written a device driver and would like to load it automatically and generate the device nodes. I wrote a config script that I would like to execute at boot and added it to rc.local. It will not run at boot up and I have spent hours researching. The file is below:
 
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
 
echo "rc.local excuted!" > ~/pcmmio/test
~/pcmmio/pcmmio_load
exit 0
 
If I execute this script from the command line, it works fine. But it does not work at boot up. The echo command is never executed.
 
The link S99rc.local did not exist in any of the runtime directories. I created S99rc.local in /etc/rc2.d and linked it to ../init.d/rc.local. This did not help. The link /etc/rc2.d/S20rc.local already existed.
 
Any suggestions why rc.local does not execute?

---

### Post by Brandon Williams on 2010-06-01
How are you running the script on the command line? If you're running it with sudo, as in:
```
sudo /etc/rc.local
```
the problem could be related to '~' expansion. Try running the script in a root login shell, like this:
```
$ sudo -i
root@host:~# sh -e
# /etc/rc.local
```
Does the script work in this case? If not, is the failure due to an unknown path? If the failure is related to the path, the try replacing '~' with the correct '/home/<user>' value.

---

### Post by pauldemet on 2010-06-01
That was it!!!!! Thanks.

---

### Post by lavinog on 2010-06-01
You should use full paths in scripts.
Also look at upstart:
man 5 init
The startup scripts go in /etc/init

---

