---
title: "Computer (host) name problem"
date: 2010-02-11
forum: General Help
---

### Post by t0p on 2010-02-11
My EeePC used to be called 'machine', but some time ago I renamed it 'deimos'.  There's been no problem with this for ages; but today I got an email 'Delivery Status Notification (Failure)' - because of a failed job, Anacron had tried to send a message to 'root@machine'.

I've checked /etc/hosts and /etc/hostname, and in both locations the computer's name is correctly configured as 'deimos'.  Where else should I look?

---

### Post by mechro on 2010-02-11
Try... **sudo grep -lR machine /etc**

I got that from here...

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1299049](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1299049)

;) ;)

---

