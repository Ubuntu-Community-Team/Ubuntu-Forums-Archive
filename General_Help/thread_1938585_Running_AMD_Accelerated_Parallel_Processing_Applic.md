---
title: "Running AMD Accelerated Parallel Processing Applications Remotely"
date: 2012-03-09
forum: General Help
---

### Post by midden on 2012-03-09
I am running 64-bit Xubuntu (11.10) and want to use an AMD Radeon 7970 GPU for parallel processing. I have things sorted out so they work when I am logged in directly; however, I cannot access my GPU when I remotely ssh or nx into the system.

According to the pdf file [here]("http://www.google.com/url?sa=t&rct=j&q=amd%20remote%20processing%20gpu&source=web&cd=1&ved=0CCsQFjAA&url=http%3A%2F%2Fdeveloper.amd.com%2Fsdks%2FAMDAPPSDK%2Fassets%2FApp_Note-Running_AMD_APP_Apps_Remotely.pdf&ei=T9daT7HmDcfL0QHsxbCeDw&usg=AFQjCNHE34Kqcww7Pfao92TXE9LPe_jhIQ&cad=rja"), this can be fixed by:

> a. Add the following lines at the end of /etc/gdm/Init/Default,
before the exit 0, to modify the security settings, allowing remote
sessions to access the X server and ensuring that remote sessions have
access to the necessary device files when communicating with the GPU:

xhost +

chmod uog+rw /dev/ati/card*

b. If you normally use bash, add the following line to the end of
/etc/bashrc file to ensure remote sessions know which X server to
access.

case $DISPLAY in ’’) export DISPLAY=:0;; *) ;; esac

NOTE: ’ ’ are two single quotes, not a single double-quote.

However, since gdm is not used anymore, I am not sure how to implement this change. Any suggestions?

---

### Post by midden on 2012-03-10
In case it helps -- when I am phsically logged in at the host machine and then ssh in from a remote machine, I am able to access the gpu; however I cannot use the -X or -Y flags when I connect.

---

### Post by philk1989 on 2012-04-17
> **midden said:**
> 
However, since gdm is not used anymore, I am not sure how to implement this change. Any suggestions?


# Original source for gdm configuration: 
[http://developer.amd.com/sdks/AMDAPPSDK/assets/App_Note-Running_AMD_APP_Apps_Remotely.pdf](http://developer.amd.com/sdks/AMDAPPSDK/assets/App_Note-Running_AMD_APP_Apps_Remotely.pdf)

/etc/lightdm/lightdm.conf
# add the following line:
```
display-setup-script=/root/configure_cl
```

# now create this file: /root/configure_cl
# you may need to add the permissions below the 'xhost' line, however the permissions were already correct in my case.
```

#!/bin/sh
xhost +
date >> /var/log/cl.log # Just to show its working

```

# make the script executable
```
chmod +x /root/configure_cl
```

# add the following line to /etc/profile
```
export DISPLAY=:0
```
# this will make X11 think it needs to forward everything local X and not the remote end.
# -> meaning X11 forwarding will not work.
# put it in your own ~/.profile, if you dont want this change to affect other users

# you may also need to add your user name to the video group in /etc/group
```
gpasswd -a <username> video
```

# if you have multiple users, use this simple for loop
```
for m in user1 user2 user3; do gpasswd -a $m video; done
```

# restart lightdm
```
/etc/init.d/lightdm restart
```

# test to see if everything worked:
# This is over SSH
```

root@host:~# /etc/init.d/lightdm restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service lightdm restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop lightdm ; start lightdm. The restart(8) utility is also available.
lightdm stop/waiting
lightdm start/running, process 6011

```
```

root@host:~# cat /var/log/cl.log
Tue Apr 17 14:15:34 CDT 2012

```
```

root@host:~# fglrxinfo 
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7900 Series 
OpenGL version string: 4.2.11566 Compatibility Profile Context

```

---

### Post by midden on 2012-04-18
Thanks for the reply! I have to admit that I resorted to installing gdm to solve this problem. Everything works fine now; howver, I will look into going back to stock with 12.04, so thank you for providing such a detailed response.

---

