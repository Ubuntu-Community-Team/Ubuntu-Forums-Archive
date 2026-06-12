---
title: "Cannot boot after 11.04 upgrade"
date: 2011-10-12
forum: General Help
---

### Post by FLCL on 2011-10-12
After upgrading to 11.04 (using dist-upgrade..which may have been stupid of me) I can not boot. 
I'm presented with 
```
init: udevtrigger main process (125) terminated with status 1
init: udevtrigger post-stop process (128) terminated with status 1
init: udevmonitor main process (124) killed by TERM signal
mountall: Disconnected from Plymouth
```

and then a blinking cursor. I cannot drop into root shell as it hangs at mountall. How can I fix this?

---

### Post by holycow131415 on 2011-10-12
I dont know, but i do suggest to...

Save hours of frustration, waiting, and maybe failure by just downloading the iso and clean installing. System will work better anyway, so just back up your stuff and clean install.

---

### Post by FLCL on 2011-10-12
Well I ended up fixing it, that part anyway. I purged fglrx video drivers and reinstalled the ATI following this: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) 
To clarify for anyone in the future, I used the live cd to mount the volume with ubuntu on it, then chroot into the mount and ran under root.

the problem now is I'm Experiencing some issues where I can log I'm but Xserver is still messed up. In console I'm getting ```
 fatal server error: could not create lock file in /tmp/.tX0-lock 
XIO: fatal IO error 11 (resource temporarily unavailable) on X server ":0" 
xauth: error in locking authority file /home/myuser/.Xauthority after 7 requests (7 known processed) with 0 events remaining. 
```

Edit: The purpose of this thread was resolved. Will start a new one

---

