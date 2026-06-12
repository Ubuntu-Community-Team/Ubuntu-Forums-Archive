---
title: "A problem with open ssh"
date: 2009-11-03
forum: General Help
---

### Post by quimica on 2009-11-03
Hey comunity! 
My problem with open ssh 4.7 is that i cant connect to another machine but i can not do it from another machines to my machine. The message is:  ssh: connect to host (my ip address) port 22: Connection refused
Really i would like to know how can i solve this problem. Please help me.

---

### Post by issih on 2009-11-03
Have you installed the server package onto your machine? by default ubuntu only has the client installed. The server package is:

"openssh-server"

so check if that is installed.

If you are trying to log in from a machine external to your LAN, have you port forwarded port 22 from the router to your machine?

Have you left the firewall settings alone? -by default the firewall (ufw) pretty much lets all traffic through, but if you've messed with it you'll need to ensure it isn't blocking port 22.

Check those, then get back to us..

---

### Post by wildweathel on 2009-11-03
Ubuntu, for security reasons, doesn't run an SSH server by default.  You have to first consider the security implications (SSH and VNC are the biggest security risks on Ubuntu), and second, install and configure openssh-server.  

I think it's a very, very good idea to use SSH keys only--not passwords--if your computer is connected to the Internet.  At the very least, make sure you have a very strong randomly-generated password.  Weak passwords connected to the Internet will eventually be cracked.  I like "apg" for password generation.  Fairly strong, yet memorable, passwords.

That said, documentation is here:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Be careful, and feel free to ask any questions you still have after reading.

---

### Post by Groover20 on 2009-11-03
Do you have a firewall running on your machine?  It looks like it's blocked...

---

