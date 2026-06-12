---
title: "Backgrounded script in /etc/rc.local not working since upgrade to Jaunty"
date: 2009-07-26
forum: General Help
---

### Post by wonk-o-matic on 2009-07-26
I background a script in /etc/rc.local, but it isn't running when I login.  

I then directed stdout and stderr to a file, and the file is created, but empty.  If I sudo /etc/rc.local, it is then running in the background.  Owner is root:root, and perms are 755.  

Any ideas?  

Thanks, 
Dan

---

### Post by BluShift on 2009-07-27
I have no idea if this helps you... but have you set it to run at startup in System > Preferences > Sessions?

I'm not sure if that's what you asking.

---

### Post by wonk-o-matic on 2009-07-28
Actually, I should have said that it doesn't seem to start at boot.  

Putting things in System > Preferences > Sessions is just for starting stuff under your own user ID.  Since the script is designed to logout piggish users, that would make it easy for them to circumvent.  

This worked fine in Hardy Heron.  Isn't breaking /etc/rc.local kind of a big deal?  It's like the old DOS autoexec.bat for Linux.  I've had users logged in for days at a time, I'm annoyed at Ubuntu for messing up something so fundamental.

---

### Post by Brandon Williams on 2009-07-28
How did you redirect stdout and stderr? On the command line within /etc/rc.local? Or inside the script itself? If it's done within /etc/rc.local, it shows you that /etc/rc.local is being run and that there is probably an issue executing the script.

You could try getting some debug output from /etc/rc.local, but I don't know how much that will help when trying to diagnose a problem with a backgrounded program. To get debug output from /etc/rc.local, add these lines to the top of /etc/rc.local after '#!/bin/sh -e':
```
exec 2> /tmp/rc.local.debug
set -x
```
This should send all stderr output from /etc/rc.local into /tmp/rc.local.debug and then turn on script trace output. Look in /tmp/rc.local.debug after boot to see if there is any useful output there.

---

