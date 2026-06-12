---
title: "SSH server stopped working after upgrade to 11.10"
date: 2011-11-22
forum: General Help
---

### Post by blandwa on 2011-11-22
I had an SSH server working on Ubuntu 10.10.  I upgraded to 11.10, and now I get "operation timed out" when I try to connect remotely.  "ssh localhost" works.  I'm pretty sure I didn't install or activate any firewalls.  Port forwarding should still be set up properly.  What might be wrong?

---

### Post by deonis on 2011-11-22
Try to Install "firewall configuration" (it's in repo) and check if your ssh port (22 or whatever) is open. It sound like you have it closed. Or try the following in terminal[COLOR=#c20cb9][B][FONT=monospace]:

 [/FONT][/B][/COLOR]netstat -anltp | grep "LISTEN"

if you see it open then try to reinstall SSH server. 

cheers

---

### Post by blandwa on 2011-11-22
Firewall Configuration says the firewall status is "Off", and there are no rules.  Here's the output of netstat:

$ netstat -anltp | grep "LISTEN"
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 127.0.0.1:36803         0.0.0.0:*               LISTEN      18507/GoogleTalkPlu
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:31416           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      1889/dropbox    
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN

---

### Post by deonis on 2011-11-24
Everything looks fine to me and I do not think that you  have a problem with ssh server since you can connect locally.  Try to install "firewall configuration", enable firewall and add exception for port 22.   

cheers

---

