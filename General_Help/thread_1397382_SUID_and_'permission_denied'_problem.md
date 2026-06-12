---
title: "SUID and 'permission denied' problem"
date: 2010-02-03
forum: General Help
---

### Post by William Fraser on 2010-02-03
Hello one and all.

I have just installed 9.10 netbook remix onto my Eeepc 901. I was previously using 9.4

Rather than clicking on shutdown icons, or going through shutdown menus, I added a keyboard shortcut to run a shell script containing the following code:
```
#!/bin/bash

init 0
```because init needs to be run as root to have the correct permissions, I set the owner and group to be root , ran chmod 711, then chmod u+s to prevent anyone altering the script, and to allow anyone to execute it with root privelidges

Since updateing to 9.10 netbook remix, I have been unable to get this to work.
I have applied the above changes but get a "/bin/bash: /usr/bin/shutdownscript: permission denied" error when I try to run my shutdown script from the terminal (nothing happens when I press the key combination asigned to the keyboard shortcut). If I run the shutdown script with sudo then it neatly shuts down. ls reveals the following permissions:
-rws--s--x 1 root root 

So it appears as if SUID and SGID are both set, and the owner/group are correct, and the script works, and yet it doesn't have the permissions to work. I installed 9.4 long ago enough that I can't remember if I had to do anything else to get it working, or has something changed between 9.4 and 9.10?

---

### Post by jken146 on 2010-02-03
Why not go for the simpler solution:
```
#!/bin/bash

sudo shutdown -h now
```

Use the higher level program *shutdown* and avoid messing with init directly.

---

### Post by Lars Noodén on 2010-02-03
jken146's suggestion will avoid the risks, dangers and problems of SUID-abuse.  ;)

Even something simple in /etc/sudoers will help

```

# allow any in group users to shutdown the machine
%users  ALL=(ALL) PASSWD: /sbin/shutdown

```

You can then use your shortcut to launch the program **shutdown** using gksudo or kdesudo.

---

### Post by William Fraser on 2010-02-06
Thanks for those suggestions :)

I now have shut down triggered by a simple 3 key combination press.

For those new to linux like me I would like to point out that that to edit the /etc/sudoers file, please use ```
visudo
``` and DON'T chmod the file so you can edit it, because this will break sudo as I found this out the hard way.

If you like me have already done this, the easiest way to fix it is to boot from a live disk, mount your root drive, and change the permissions back before rebooting...

---

