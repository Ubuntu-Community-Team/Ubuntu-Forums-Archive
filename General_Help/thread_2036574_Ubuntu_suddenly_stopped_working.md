---
title: "Ubuntu suddenly stopped working"
date: 2012-08-02
forum: General Help
---

### Post by joblafors on 2012-08-02
Hello.
Suddenly out of nowhere I cant start my Ubuntu.

It shows Ubuntu loading screen, after that just black screen, with some text on it...

* Something about Apache [ OK ]
* Starting anac(h)ronistic com [ OK ]
* Stopping anac(h)ronistic com [ OK ]
* Checking battery state... [ OK ]
* Stopping System V runlevel compability  [ OK ]

After that just blinking cursor and it wont go any further.

---

### Post by TheFu on 2012-08-02
A few questions to get the help flowing .... 

* Which OS?  /etc/lsb-release has it.
* Server or Desktop?
* What do the log files say in /var/log?  Without a very specific error, we can't help too much.  syslog and dmesg are usually the places.  Look at the bottom of the files.
* Anything specific about your hardware that you think is important? Is it a laptop or desktop, ... 
* Did you install any new or updated software since the last reboot? Could that be the issue?
* Can you force a manual fcsk? You may need a live boot CDROM/flash to accomplish this.
* Could you be out of disk storage or inodes?  Check with **du -s / **and **du -i /**
* Does a different console work?  In a non-GUI state, you can change consoles  [http://linux.about.com/od/ubuntu_doc/a/ubudg24t8.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t8.htm) seemed to be the shortest explanation.

When you find the solution, please come back to this thread, explain the solution, and mark it [SOLVED] to help the next guy.

---

