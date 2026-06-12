---
title: "Can I swap SSH Client to a Server?"
date: 2010-05-16
forum: General Help
---

### Post by Twotoes on 2010-05-16
Have a laptop with Ubuntu 10.4 and a dual boot desktop with Ubuntu 9.10 and 10.4. Using wifi on laptop.
Before upgrading to 10.4 the desktop was the server and the laptop the client. Unfortunately when I setup ssh in 10.4 on the desktop I made it the client instead of the server. Reinstalled 10.4 on the desktop but it still remains the client. Booting the desktop into 9.10 the laptop is the client and the desktop is the server.
How can I change Ubuntu 10.4 on the desktop to be a server?

---

### Post by XCan on 2010-05-17
I'm not sure I understand. To turn a machine to accepting ssh connections you simply have to configure the daemon, sshd. Make sure you've double checked /etc/sshd.config and that sshd is running on your server box.

---

### Post by efflandt on 2010-05-17
The openssh client is installed by default, the opensshd server is not.  So all you have to do is use Synaptic to install **openssh-server**.  Then see /etc/sshd if you want to configure anything and **sudo service ssh restart** after making any config changes.

I usually disallow root login and passwords (to require keys only).

---

### Post by Twotoes on 2010-05-17
Thanks for replies. Installed openssh-server but the information in /etc/ssh is beyond me so wouldn't know what to change.

---

