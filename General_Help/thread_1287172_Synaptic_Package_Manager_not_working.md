---
title: "Synaptic Package Manager not working"
date: 2009-10-09
forum: General Help
---

### Post by Haug219 on 2009-10-09
Whenever I try to open Synaptic Package Manager it says E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem .......Also I cant download anny apps because it says other things are running and I cant find anything else that is running no update tools or anything.

---

### Post by aheckler on 2009-10-09
Open up the Terminal and run "sudo dpkg --configure -a". After that, just log out and log back in tand try again.

---

### Post by Haug219 on 2009-10-09
That worked thank you so much

---

### Post by isubbareddy on 2010-12-13
sudo dpkg --configure -a  is not working in Ubuntu-10.4 desktop version in my computer. Synoptic manager and root terminal are not working. Help me in this regards.

Error message is :sudo must be  setuid root

---

### Post by karthick87 on 2010-12-13
> **isubbareddy said:**
> sudo dpkg --configure -a  is not working in Ubuntu-10.4 desktop version in my computer. Synoptic manager and root terminal are not working. Help me in this regards.

Error message is :sudo must be  setuid root


Run the following in terminal,
```
chown root:root /usr/bin/sudo
```
```
chmod 4111 /usr/bin/sudo
```

---

### Post by ahmedmutahar on 2010-12-18
i really need help with this ... 

i tried all the possible ways to install my graphic card in ubuntu 10.10 but i couldn't 

i got message in the terminal said that envyng can't be located... and whenever i try to open ( Synaptic Package Manager ) the system freezes and hang.. but the mouse still moving...

same happened when i tried to change desktop background...


could anyone please help me? ..

---

