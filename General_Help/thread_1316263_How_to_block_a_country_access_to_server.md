---
title: "How to block a country access to server"
date: 2009-11-05
forum: General Help
---

### Post by geoffmcc on 2009-11-05
Hello. I am just wondering. I have since moved the ssh port to something custom but during my stay on port 22 i noticed that most logon attempts came from china. Can i block china access completely (www ssh anything) from iptables or something, anyone do this?

---

### Post by undecim on 2009-11-05
SSH attacks will come from all countries as long as you have SSH set to listen on the default port 22. Changing the port, as you have done, is the best thing to do to stop them.

As far as blocking a country, I don't know, but you should be able to block IP address ranges with sshd_config

---

### Post by lovinglinux on 2009-11-05
Use [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/) with [this blocklist](http://iblocklist.com/list.php?list=cn) or compile your own list with [this service](http://www.countryipblocks.net/).

---

### Post by uljanow on 2009-11-05
Check out [iplist]("http://ubuntuforums.org/showthread.php?t=530183") which comes with 25 country list.

---

### Post by geoffmcc on 2009-11-06
thanks for suggestions. will check them out.

---

