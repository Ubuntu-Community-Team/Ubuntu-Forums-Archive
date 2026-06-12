---
title: "VNC cant connect"
date: 2011-01-08
forum: General Help
---

### Post by ahmed470 on 2011-01-08
I cant connect to VNC server on my ubuntu machine?
Actually I can when I go and physical login that machine. But if I reboot the machine then I cant login unless go to the machine itself and physically login to that machine.
How can I connect to vnc without first manually logging in to my machine?

---

### Post by tredegar on 2011-01-08
You need to start a vnc server on the machine when it boots.

Put something like this in **/etc/rc.local** on the line before the final **exit 0**
```
# Start a vnc server for the user ahmed
su - ahmed -c "cd /home/ahmed && vncserver -geometry 1024x768 -depth 24 :1"
```
Connect to it at **machine:1**

---

### Post by ahmed470 on 2011-01-08
Nope this didnt work.

VNC error: unable to connect to host: Connection refused (10061)

---

