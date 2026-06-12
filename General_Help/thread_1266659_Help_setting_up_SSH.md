---
title: "Help setting up SSH"
date: 2009-09-14
forum: General Help
---

### Post by shoenigman on 2009-09-14
I recently installed a headless version of Ubuntu (mini) in order to build an Asterisk PBX. I want to SSH from a laptop running Hardy Herron. How do I do this? Do I need to install anything on the PBX for SSH? How do I know that it is configured correctly? Then what do I need to do on the laptop? What commands do I execute in the terminal? 

Thanks for any assistance in advance!

---

### Post by P4man on 2009-09-15
an ssh client is installed by default, but you need to install an ssh server

```
sudo apt-get install openssh-server
```

Then to connect to it from the client,  just enter:

```
ssh username@computer (name or IP address)
```

---

### Post by jondkent on 2009-09-15
The config for sshd (the ssh daemon) is is /etc/ssh and called sshd_config.  Worth having a look at this once you have followed P4man instructions on installation, as there are various options you may want to en|disable.

---

### Post by P4man on 2009-09-15
Or have a look here:
[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

---

### Post by shoenigman on 2009-09-24
I am sorry that it took so long to respond but I really appreciate your help. I feel stupid since this ended up being such a trivial task. Anyway, once again thanks!

---

