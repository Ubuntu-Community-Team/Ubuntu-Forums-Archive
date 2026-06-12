---
title: "How to Get to the Shell Booting Up..."
date: 2010-02-13
forum: General Help
---

### Post by wbee on 2010-02-13
Hello,

In the process of getting a screen resolution issue settled,I have tried accessing.

```
sudu nvidia-xconfig 
``` to no avail.

Finally,I tried,

```
`sudo nvidia-xconfig`
```

and got this:

```
wbee@wbee-desktop:~$ sudo `nvidia-xconfig`
The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-glx-173
 * nvidia-glx-185
 * nvidia-glx-96
Try: sudo apt-get install <selected package>
nvidia-xconfig: command not found
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
wbee@wbee-desktop:~$ 

```

The problem is the last time I tried to load nvidia drivers,it just made things worse. So bad,in fact,that when I rebooted,my monitor told me it could not process it because it was "outside of range".

----------

So,is there a way I can access the terminal at boot,from the grub,and if so,how?

------

Thank you.

---

### Post by falconindy on 2010-02-13
dbl post

---

### Post by falconindy on 2010-02-13
You shouldn't be encasing 'nvidia-xconfig' in backticks.

To answer your actual question though, append 'text' to your kernel options in GRUB (w/o the quotes).

---

