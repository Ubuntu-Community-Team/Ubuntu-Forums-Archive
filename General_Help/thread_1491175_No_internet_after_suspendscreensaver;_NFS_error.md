---
title: "No internet after suspend/screensaver; NFS error?"
date: 2010-05-23
forum: General Help
---

### Post by Bucky Ball on 2010-05-23
Hi all,

Issues with one of the computers:

8.04 LTS, 
Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Compaq 610 laptop

Seems that when the computer comes out of suspend there is no network. So switch off suspend and set screensaver. Same. If you leave the room for half an hour it happens even if they are both off. Have hunted for a fix but nothing's worked. Might have something to do with my NFS set up.

This is kind of in two parts. 
Is the problem with the wireless module not restarting after suspend (how do I check for sure?)?
or ...
Could my NFS network setup have something to do with the issue or separate problem? When I restart the network I get this error and it takes awhile:

```
anna@katie:~$ sudo /etc/init.d/networking restart
[sudo] password for anna: 
 * Reconfiguring network interfaces...                                           * Starting portmap daemon...
 * Already running.
   ...done.
 * Starting NFS common utilities
   ...done.
mount.nfs: internal error
mount.nfs: internal error
```The server is a desktop and is not always on so laptop client sluggish and always throws this error when its off. Any way of getting rid of that problem? The other client on the network doesn't have that problem and still shows the share icons on the desktop when the server is not on. Just shows them as empty. On the laptop there are no icons if the server is off. Strange cos the two clients are set up the same way as far as I can see. 

Any ideas, suggestions, regarding if these two are related? Really want to fix this wireless drop out issue.

---

### Post by bobcollard on 2010-05-23
Check out this thread, Chaosgrimm has a solution.
[http://ubuntuforums.org/showthread.php?t=1451064](http://ubuntuforums.org/showthread.php?t=1451064)

---

### Post by Bucky Ball on 2010-05-23
Thanks for that but the files mentioned in the fix in the link to check and alter don't exist for me. Wondering if they are specific to 10.04. Using 8.04.

Also wonder if I should create those files and add the changes ...

---

### Post by Bucky Ball on 2010-05-23
I do have this in:

```
 /usr/lib/pm-utils/sleep.d/10NetworkManager
```... though.

```
#!/bin/bash

. /usr/lib/pm-utils/functions

suspend_nm() {
    # Tell NetworkManager to shut down networking
    dbus-send --system                         \
        --dest=org.freedesktop.NetworkManager  \
        /org/freedesktop/NetworkManager        \
        org.freedesktop.NetworkManager.sleep
}

resume_nm() {
    # Wake up NetworkManager and make it do a new connection
    dbus-send --system                        \
        --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager       \
        org.freedesktop.NetworkManager.wake
}

case "$1" in
    hibernate|suspend)
        suspend_nm
        ;;
    thaw|resume)
        resume_nm
        ;;
    *)
        ;;
esac

exit $?
```

Hmm? Any anomalies?

---

### Post by Bucky Ball on 2010-05-24
Bump. Getting nowhere fast with this. Wife's computer and very frustrating running sudo /etc/init.d/networking restart after you've left the machine for twenty minutes. 

Interestingly, when that command is executed, it takes an age to ask for the password. Any other sudo command pops up asking for the password pronto.

What I'd really like to discover is if this is related to NFS mount error or there is a problem with the network connection itself. Maybe Wicd might be worth a try.

---

### Post by Bucky Ball on 2010-05-28
Bump ...

---

