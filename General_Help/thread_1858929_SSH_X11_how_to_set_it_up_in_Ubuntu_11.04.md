---
title: "SSH X11 how to set it up in Ubuntu 11.04"
date: 2011-10-13
forum: General Help
---

### Post by mancora on 2011-10-13
Dear Friends,

I need your help here. I am running ubuntu 11.04 and I didnt have any problem running x11 and ssh, but from one day to another it did stop working. I had been doing different things and I haven't been able to fix it. So my question is if somebody can point me out how should I approach this problem from zero. From authorization, set up display variable, and make the connection. I have read different documents but the information is diverse and not consistent 

I deleted my .Xauthentication file in my directory and I can not find how to set it up again.

server01:~$ xhost +
xhost:  unable to open display ""

@server01:~$ xauth info
Authority file:       /home/USER/.Xauthority
File new:             no
File locked:          no
Number of entries:    0
Changes honored:      yes
Changes made:         no
Current input:        (argv):1
@server01:~$ xauth list

@server01:~$ ps aux | grep auth
root      3588  0.0  0.1 120768 12760 tty7     Ss+  13:27   0:00 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-xIL2s6/database -nolisten tcp vt7

Thanks in advance,
Christian

---

