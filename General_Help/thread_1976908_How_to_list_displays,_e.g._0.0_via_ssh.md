---
title: "How to list displays, e.g. :0.0 via ssh"
date: 2012-05-09
forum: General Help
---

### Post by Azdour on 2012-05-09
Hi,

I have a script that sends a message via SSH that pops up a dialog on the target computer. Under Ubuntu I would use SSH and issue the 'who' command to get the displays currently active, e.g. :0.0 etc...

Now I'm trying to do the same thing with Xubuntu 12.04 the who command does not return the list of logged in users via ssh.

Via ssh is there any other way to query the target computer for a list of displays?

---

### Post by Toz on 2012-05-09
> **Azdour said:**
> Now I'm trying to do the same thing with Xubuntu 12.04 the who command does not return the list of logged in users via ssh.
This bug may be of interest to you: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/870297"). There is no resolution of yet, but basically lightdm isn't logging to wtmp meaning the who and w no longer display logged in users. Feel free to add your name to the list of affected users.

---

### Post by papibe on 2012-05-09
Hi Azdour.

Take a look at posts #5 and #6 of this [thread]("http://ubuntuforums.org/showthread.php?t=1831847&highlight=%2Fusr%2Fbin%2FX+awk").

I hope that points you in the right direction.
Regards.

---

### Post by Azdour on 2012-05-10
Hi Papibe,

Thanks, that was exactly what I was looking for.

---

