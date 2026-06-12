---
title: "Starting services at boot"
date: 2011-10-28
forum: General Help
---

### Post by malcmail on 2011-10-28
I've just installed lubuntu 10.04 as a base for a small home server (a long story in itself!). I've sorted my apache and also installed webmin but I can't get either to start at boot. I've had a look in the /etc/rc3.d folder to find a webmin link but no apache link. I've tried adding "/etc/init.d/webmin start" in the /etc/rc.local file as well but nothing seems to work. Even cheating, going into webmin and clicking it to start on boot doesnt work - although to be fair it does still show it wont start on boot.

Anyone any ideas?

---

### Post by dcstar on 2011-10-28
> **malcmail said:**
> I've just installed lubuntu 10.04 as a base for a small home server (a long story in itself!). I've sorted my apache and also installed webmin but I can't get either to start at boot. I've had a look in the /etc/rc3.d folder to find a webmin link but no apache link. I've tried adding "/etc/init.d/webmin start" in the /etc/rc.local file as well but nothing seems to work. Even cheating, going into webmin and clicking it to start on boot doesnt work - although to be fair it does still show it wont start on boot.

Anyone any ideas?

Ubuntu uses rc2.d

---

### Post by malcmail on 2011-10-28
I should add that sysv-rc-conf shows both to be due to start at run level 2 and 5, if that makes any difference at all.

---

### Post by malcmail on 2011-10-28
> **dcstar said:**
> Ubuntu uses rc2.d

I'll double check in there then - cheers. Although the sysv-rc-conf shows both to run at level 2 as well :(

---

### Post by malcmail on 2011-10-28
Yet more info - in rc2.d there are 2 links to apache2 and 4 (!?!?!) to webmin. These are the only ones with duplicates. Could this be the problem?

---

### Post by malcmail on 2011-10-28
When I check runlevel if returns unknown. My guess is that this is the problem. If it can't work out what runlevel is on it won't pick up the right services will it? ALthough it still seems to start SSHD. Just thinking out loud (kind of!)

---

### Post by malcmail on 2011-10-28
Looks like I've sorted in - in case anyone else is having a similar problem try here:-

[http://ubuntuforums.org/showthread.php?p=9213567](http://ubuntuforums.org/showthread.php?p=9213567)

ALthough the first psot didnt work for me the one changing the interface, in my case to wlan0, did.

---

