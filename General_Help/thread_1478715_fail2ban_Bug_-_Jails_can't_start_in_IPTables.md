---
title: "fail2ban Bug - Jails can't start in IPTables"
date: 2010-05-10
forum: General Help
---

### Post by eXDee on 2010-05-10
Currently suffering from this bug:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=554162](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=554162)

If you don't want to read the whole thing, it appears fail2ban overloads IPTables when you have too many jails, and sends a whole load of commands at once.

I attempted to use the workaround making it sleep for a random period of time, but this does not help at all, it still fails like it used to.

Any ideas? Fail2ban is a pretty popular app...

Ubuntu 9.10.

```
$ aptitude show fail2ban
Package: fail2ban
State: installed
Automatically installed: no
Version: 0.8.3-6ubuntu2
```
I see 0.84 has been out for a while, though in my experience building from source has always been an issue as we're in an OpenVZ VPS environment, so it always seems to create errors.

---

### Post by GemCoder on 2010-07-15
Solved it today with this info:

[http://www.fail2ban.org/wiki/index.php/Fail2ban_talk:Community_Portal](http://www.fail2ban.org/wiki/index.php/Fail2ban_talk:Community_Portal)

"fail2ban.action.action ERROR on  startup/restart

I had multiple fail2ban.action.action ERROR on startup/restart. It  seems there was a "race" condition with iptables. I solved the problem completely on my system by editing  /usr/bin/fail2ban-client and adding a time.sleep(0.1) 
	def __processCmd(self, cmd, showRet = True): 

beautifier = Beautifier() 

for c in cmd: 

**time.sleep(0.1)** 

beautifier.setInputCmd(c)"


works for me like a charm :)

---

