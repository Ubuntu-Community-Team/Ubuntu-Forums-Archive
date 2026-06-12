---
title: "Cannot self-ssh"
date: 2010-10-26
forum: General Help
---

### Post by hwttdz on 2010-10-26
I'm having trouble connecting to one of my machines.  Port forwarding is up and working (i.e. I can reach the webserver).  But I can't connect by ssh.  At the machine 

ssh 127.0.0.1
ssh: connect to host 127.0.0.1 port 22: Connection refused

it's possible it's due to something in the hosts file? because I remember editing that recently, but I also remember connecting to the machine after doing so.  So I can't figure.  I believe I also connected to the machine after updating to 10.10 (which I only did a few days ago).  Any ideas?

---

### Post by hwttdz on 2010-10-26
Might have been that I didn't have a newline at the end of the file, might have been my keepalive syntax was incorrect, but removing a timeout option, adding a newline and restarting ssh server fixed the issue.

---

