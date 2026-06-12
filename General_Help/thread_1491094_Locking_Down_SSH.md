---
title: "Locking Down SSH"
date: 2010-05-23
forum: General Help
---

### Post by aeternitas on 2010-05-23
I find myself using SSH from my mobile phone to manage administrative tasks when I'm away--completing updates and the like, things that can be done during normal usage but sap my RAM and CPU to the point of frustration, given the hardware I've got to work with. It's convenient, I can do what I wish (without the benefit of an X session) while I'm at work. 

The issue I run into is the fact that my auth.log is littered with items like this:
```
May 16 12:53:17 BETA sshd[18941]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=200.111.184.180 
May 16 12:53:19 BETA sshd[18941]: Failed password for invalid user lala from 200.111.184.180 port 41787 ssh2
May 16 12:53:25 BETA sshd[18943]: Invalid user master from 200.111.184.180
```Which tells me that some inconspicuous person and/or botnet keeps trying to get into my system.  This is generally annoying; at this point, my system isn't used for anything particularly critical; however, the fact that only failures or questionable successes--such as those from my mobile, the IP and Host of which can vary a fair bit (and the host resolution almost always fails, based on the way the IP/Host advertisement is presented to an external host is established--it's essentially manufactured)--doesn't tell me who/what has figured it out.  I've done what I can to tamp down SSH access to the system, root is blocked via SSH (a moot item, since root isn't allowed locally), I've limited only my own username as allowed to connect via SSH...all it would take, though, is an alphanumeric dictionary that hits the right combination to get a password prompt, and to be able to brute-force it from there.

Overall, I know there's few, if any ways, to prevent someone attempting to get into my system via SSH; what additional steps can I take to minimize the possibility that I might end up compromised?

---

### Post by thebigob on 2010-05-23
[http://callum.mine.nu/mediawiki/index.php/Security](http://callum.mine.nu/mediawiki/index.php/Security)

How I do mine :)

---

