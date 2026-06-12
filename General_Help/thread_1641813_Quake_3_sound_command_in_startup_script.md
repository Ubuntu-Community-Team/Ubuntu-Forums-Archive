---
title: "Quake 3 sound command in startup script?"
date: 2010-12-09
forum: General Help
---

### Post by FA-MAS on 2010-12-09
So i've installed Quake 3 on my Ubuntu 10.10 (Maverick) system.  I get no sound unless I run the echo command to map to the oss sound device.  You know, this one.

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss && quake3

I have a couple problems that I need help with.

First. That command gives access denied when i run it as normal user, or when i sudo
It has to be run as root.  I can change permissions on /proc/asound/card0/pcm0p/oss to allow it to run as regular user, but the permissions reset upon reboot.

Second.  I'd like to have that run automatically at boot.

So my question is, is there a script that I can add this to that's automatically run as an elevated user or system process that will run these commands so I don't have to?

---

### Post by FA-MAS on 2010-12-10
Anyone?  I'm not looking for Quake specific answers.  There's got to be a script that runs before or after session starts so this command can be automatically run, whilst not having to su to do it.

---

### Post by tommcd on 2010-12-10
> **FA-MAS said:**
> 
Second.  I'd like to have that run automatically at boot.
So my question is, is there a script that I can add this to that's automatically run as an elevated user or system process that will run these commands so I don't have to?
You can try adding your command to the */etc/rc.local* file.
As it says in the comments to that file:
```
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```
So try adding the command above the *exit 0* line. Then make sure that */etc/rc.local* is executable.

---

### Post by FA-MAS on 2010-12-11
Yep, that sorted it.  Thanks alot!

---

