---
title: "Craziest Thing"
date: 2009-12-26
forum: General Help
---

### Post by bmachia on 2009-12-26
Since upgrading to Jaunty Jackalope I have the strangest problem.  /etc/rc.local appears to not be called at boot.   I primary use rc.local to bring wlan0 up and and attach to my WiFi.  

After logging on, I can manually command line /etc/rc.local and it performs perfectly.

rc.local permissions are;
-rwxr-xr-x 1 root root 626 2009-12-26 12:30 /etc/rc.local

Can anyone offer suggestions or thoughts so I can diagnose and fix this problem?

Bill

---

### Post by john newbuntu on 2009-12-26
First make absolutely sure that it is not getting called, perhaps with a simple statement at the beginning and end of the rc.local file like:
echo "From rc.local at `date`" >> /home/<user>/rcl.log
I say this because there was a bug reported for jobs getting killed when this script is exited:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/332210](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/332210)

---

### Post by dcstar on 2009-12-27
> **bmachia said:**
> Since upgrading to Jaunty Jackalope I have the strangest problem.  /etc/rc.local appears to not be called at boot.   I primary use rc.local to bring wlan0 up and and attach to my WiFi.  

After logging on, I can manually command line /etc/rc.local and it performs perfectly.

rc.local permissions are;
-rwxr-xr-x 1 root root 626 2009-12-26 12:30 /etc/rc.local

Can anyone offer suggestions or thoughts so I can diagnose and fix this problem?

Bill

9.10 now starts things asynchronously to speed up the boot process, so rc.local is probably run before the things it tries to do are actually ready to be used.

Put a delay before running the commands and see what happens.

This is what happens when developers pander to the "I want faster boot times" faction even though it stuffs up other things and it still takes exactly the same amount of time to get a fully functional system loaded.

---

