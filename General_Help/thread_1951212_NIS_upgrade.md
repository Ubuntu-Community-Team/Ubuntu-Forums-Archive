---
title: "NIS upgrade"
date: 2012-04-02
forum: General Help
---

### Post by cardogar on 2012-04-02
Hola my dear ubuntu experts,

I need your help in order to solve an error in an update that is destroying my life.

A brief summary of my problem:

I have installed an ubuntu 10.04.4 in my computer at the office. My user is not a local user, it is a user in a local network. Everything worked fine until last week when I tried to install a regular update.

In particular, the system was upgrading NIS. But the update frozen. After few hours the update was still pending, so I decided to kill it... bad done.

After rebooting, I couldn't log in. NIS seemed to be damaged and I couldn't find in google any help.

If I try to apt-get update my system being root, this message appears:

Unpcaking replacement nis ...
Preparing to replace autofs5 5.0.4-3 (using .../autofs5_5.0.4-3.1ubuntu5.2_amd64.deb) ...

forever and ever... I cannot cancel it, I only can reboot the system or log in as root (or local user, I created one but I cannot work since all my tools are in the local network) in another session.

I'm totally lost... I would really appreciate so much any help with this.

Thanks a lot.

---

### Post by cardogar on 2012-04-02
I managed to downgrade NIS to the previous version, however autofs doesn't work yet.

I cannot install it, otherwise everything crash again.

So far, I have to hard mount the network folders...

I do not still know why I cannot update NIS and what is happening with autofs...

Nightmare.

---

### Post by raja.genupula on 2012-04-02
ok do this in terminal 
```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by cardogar on 2012-04-02
Thanks for your reply, but it's not that simple.

If I do "dpkg --configure -a", automatically the system tries to update nis (autofs5) and gets frozen again.

---

### Post by CynicRus on 2012-04-02
sudo dpkg -P autofs5_5.0.4-3.1ubuntu5.2_amd64
sudo dpkg --configure -a

---

