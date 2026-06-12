---
title: "Xorg CPU usage spikes on x11vnc connection"
date: 2011-03-28
forum: General Help
---

### Post by brandn487 on 2011-03-28
Hello,

My CPU usage is normal until I connect to the VNC server from another machine. When I am in the VNC session, Xorg CPU usage stays between 75% - 100% until it eventually crashes, bringing me back to the login screen.

I am on fully updated Ubuntu 10.10. I have an AMD X2 3800+, with 1 GB of RAM. My video card is an nVidia GeForce4 MX 4000 and I am using the proprietary nVidia Accelerated Graphics Driver (version 96) [recommended]. I have only installed x11vnc, samba, and webmin.

I didn't notice any problems in Xorg.log

I am starting x11vnc with this command in /etc/gdm/Init/Default:

```
sudo /usr/bin/x11vnc -safer -forever -o /var/log/x11vnc.log -rfbauth /home/brandon/.vnc/passwd -bg
```

I am looking for some advice on how I can troubleshoot this. Any help is greatly appreciated.

Thank you!

---

### Post by krunge on 2011-03-29
There is a bug in the Xorg server that makes it go into an infinite recursion based on a request that x11vnc makes.  Maybe this is your problem.  One can work around the problem by adding this to the x11vnc cmdline:
```
-noxrecord
```
There are some other, older, Xorg bugs that can be worked around with these x11vnc cmdline options:
```
-noxfixes -noxdamage
```
Try all 3 to see if it works around your failure.  You can search these forums for those 3 terms to get more information about the Xorg bugs.

---

### Post by brandn487 on 2011-03-30
Well, I tried those x11vnc options and it didn't seem to have much affect. Xorg CPU usage is still very high and therefore unusable. Thank you kindly for the suggestion.

Perhaps there is a way to increase the verbosity of xorg logging. Then maybe I can see what it is working so hard on.

---

### Post by brandn487 on 2011-03-31
I built the latest version of x11vnc (0.9.13) from source but the problem persists.

---

