---
title: "SSH Connection reset by client error"
date: 2011-01-30
forum: General Help
---

### Post by alphaforce125 on 2011-01-30
Hello,

I'm having problem running open SSH. I have installed SSH, on my system, but when I run:

ssh localhost
I get the error :Read from socket failed:Connection reset by peer

I get that same error when trying to connect from a different local computer.

When I attempted to restart the service by typing:
sudo /etc/init.d/ssh restart

I get the following errors:

Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Restarting OpenBSD Secure Shell Server: sshd Could not load host key:/etc/ssh/ssh_host)rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key

I proceeded to generate a new set of keys by running, ssh-keygen -b 1024

But I get the same errors after doing so.

Any help on how to get SSH running would be greatly appreciated.

---

### Post by alphaforce125 on 2011-01-30
Resolved:

Source:
[http://www.cyberciti.biz/faq/howto-regenerate-openssh-host-keys/](http://www.cyberciti.biz/faq/howto-regenerate-openssh-host-keys/)

sudo /bin/rm /etc/ssh/ssh_host_*
sudo dpkg-reconfigure openssh-server


Worked like a charm.

---

