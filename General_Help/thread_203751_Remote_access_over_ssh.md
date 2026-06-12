---
title: "Remote access over ssh"
date: 2006-06-25
forum: General Help
---

### Post by KubuntuKilledMe on 2006-06-25
Has anyone set this up successfully to do remote access over ssh?

[http://wiredx.net/index.php](http://wiredx.net/index.php)

---

### Post by digby on 2006-06-25
Yes.  All you really need on the sever end is the openssh-server package (in the apt repositories).  When you install this, it sets up X forwarding automatically.  After it's installed, all you have to do to start it is ```
sudo /etc/init.d/ssh start
```or```
sudo /usr/sbin/sshd
```

---

### Post by mrcowcow on 2006-06-25
Actually, it should start automatically after you install it from apt-get. *sudo apt-get install ssh* will get you the open-ssh server and the ssh client.

---

