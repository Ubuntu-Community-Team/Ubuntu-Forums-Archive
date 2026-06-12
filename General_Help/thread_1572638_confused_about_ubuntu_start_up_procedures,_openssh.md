---
title: "confused about ubuntu start up procedures, openssh-server"
date: 2010-09-11
forum: General Help
---

### Post by hogu on 2010-09-11
So, I installed opensshserver, becuase I want to be able to start up ssh services manually

sshd always starts up on boot up - how do I stop this?

I'm quite confused by how ubuntu does start up these days, I opened sysvconfig, and ssh isn't listed in it at all, I've got an ssh sscript in /etc/init.d - so I chmod u-x it, like it says in ubuntu docs -but sshd still starts up on boot

how do I turn this off?

and what is the right way to manage ubuntu boot up services?

thanks.

---

### Post by Sin@Sin-Sacrifice on 2010-09-11
[http://www.liberiangeek.net/2010/05/how-to-start-stop-services-in-ubuntu-lucid-automatically/](http://www.liberiangeek.net/2010/05/how-to-start-stop-services-in-ubuntu-lucid-automatically/)

---

### Post by hogu on 2010-09-11
that link refers to sysv-rc-config, 


ssh isn't listed in sysv-rc-config on this machine..... I don't know why..

---

### Post by bodhi.zazen on 2010-09-12
Ubuntu now uses upstart

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

You will need to edit /etc/init/ssh.conf and change the start / stop conditions.

---

### Post by v1ad on 2010-09-12
o in fedora i used chkconfig, its in the repositories. 
```

sudo aptitude install chkconfig
chkconfig service on


```

---

