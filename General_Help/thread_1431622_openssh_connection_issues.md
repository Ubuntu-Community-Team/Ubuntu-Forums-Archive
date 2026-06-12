---
title: "openssh connection issues"
date: 2010-03-16
forum: General Help
---

### Post by asterix299 on 2010-03-16
Hello,

I am having a strange issue with openssh on ubuntu server 9.10 64-bit. I have set up the basic installation which works fine on all of my machines except one. I can usually connect to this machine just fine but I'll go to another screen for a second, and go back to putty which will then give me an error stating "Software has caused connection abort." It also sometimes gives me this error when I try to initially connect, but not always. This is not limited to putty, anything that tries to connect through ssh gives similar errors at seemingly random times. 

What is going on here and why is only this machine affected? The only thing different on this machine is that it has an nForce3 firewall on the motherboard. At first I thought this might be causing the problem, but I changed to a PCI ethernet card and the problem persists.

---

### Post by soltanis on 2010-03-16
It is not unusual that SSH connections will time out if you leave them idle. For example, I usually have to restart connections that I left open for more than 2 minutes, because the firewall in my router will forget about the session after that amount of time and if more packets try to go through, they are dropped.

To avoid this, try setting a keep-alive interval on your server, which will hold the connection open.

[http://embraceubuntu.com/2006/02/03/keeping-ssh-sessions-alive/](http://embraceubuntu.com/2006/02/03/keeping-ssh-sessions-alive/)

Your interval need not be 5 seconds; 60 seconds worked out well for me.

---

### Post by asterix299 on 2010-03-16
This does not seem to be the problem because it will disconnect in seconds. Literally, I will go from putty to my browser and back and it will have disconnected. Plus, like I said, this error happens when I try to connect sometimes, and the other machines on the same network are not having this issue.

---

