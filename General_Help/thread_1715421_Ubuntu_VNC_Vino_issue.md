---
title: "Ubuntu VNC Vino issue"
date: 2011-03-26
forum: General Help
---

### Post by phanophite on 2011-03-26
I installed Ubuntu version 10.10 recently and I like it.  I connect to my ubuntu system through TightVNC on a windows vista laptop.  I would like to switch users and not lose my VNC connection.  As soon as I switch users, my screen goes blank and I cannot see anything on my Ubuntu machine.  As soon as I go downstairs and move the mouse or press a key on the Ubuntu machine, the image comes up on the laptop and I can log in.

It almost seems like the VNC server stops running when I switch users.  Can anyone confirm this?  I would like to connect via TightVNC from a Windows Vista laptop to a machine running Ubuntu 10.10 and switch users without having to go downstairs and move the mouse on the Ubuntu machine.

I use the default VNC server (Vino) that comes with Ubuntu 10.10.  More info below:

/etc/init$ apt-cache policy vino
vino:
  Installed: 2.32.0-0ubuntu1.1
  Candidate: 2.32.0-0ubuntu1.1
  Version table:
 *** 2.32.0-0ubuntu1.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main i386 Packages
        100 /var/lib/dpkg/status
     2.32.0-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main i386 Packages


Thanks!

---

### Post by phanophite on 2011-03-26
I found this article on another site.  It seems it may help.  I will probably give this a shot tomorrow and let you know how it goes.

[http://www.ubuntux.org/vnc-as-a-system-service](http://www.ubuntux.org/vnc-as-a-system-service)

---

