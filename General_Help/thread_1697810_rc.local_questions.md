---
title: "rc.local questions"
date: 2011-03-01
forum: General Help
---

### Post by buffchick on 2011-03-01
Linux noob here. I'm trying to run a perl script at startup and in the installation directions it says to put the path in my rc.local.

there is one in /etc and the other in /etc/init.d. Which one should I use and where should I add the path in the script?

The directions say ```
#  6. GET YOUR OS TO RUN IT ON BOOT
#    - Linux: edit /etc/rc.local or /etc/init.d/rc.local, and add:
#      /path/to/script/dreamdns.pl --daemon

```any help is greatly appreciated! THANKS!

---

### Post by buffchick on 2011-03-02
Just following up on this to see if anyone had any thoughts...

---

### Post by Krytarik on 2011-03-02
Put it into "/etc/rc.local", because "/etc/init.d/rc.local" is actually a script which runs the aforementioned.

Place the command before "exit 0":
```
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

/path/to/script/dreamdns.pl --daemon

exit 0
```Make sure to specify the correct path and that the script file is also marked as executable in its permissions.

---

### Post by buffchick on 2011-03-02
Thank you! I thought it was that simple but wasn't sure if I put it before or after the zero!

---

