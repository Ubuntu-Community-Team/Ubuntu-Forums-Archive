---
title: "Editing /etc/sudoers, don't want to mess up again."
date: 2011-02-16
forum: General Help
---

### Post by ianc1 on 2011-02-16
I edited my /etc/sudoers file the other day to add timestamp_timeout=0 to cause sudo to ask for a password every time.  I used visudo in sudo mode and when it came to saving it appeared to want to save the file as sudoers.tmp so I edited this to sudoers.  Anyway some how may edit failed.  I booted up into terminal and reedited and somehow lost all access to the sudo mode.  I think the file ended up with the wrong permissions.

After a fresh install I don't want to mess this up again.  So please, please tell me how to save it.  Should I save as sudoers.tmp or sudoers?  I presume a could have made a typo, but am assuming not.

Any help ideas would be greatly appreciated as I don't want to reinstall ubuntu and all the packages again.

Thanks

---

### Post by SavageWolf on 2011-02-16
You should be able to access the sudoers file from a live CD... If you break it, just boot from a live CD and fix it.

---

### Post by WorMzy on 2011-02-16
Just save it as the tmp file, visudo checks the validity of this file after you exit, and if it's invalid, gives you the option to modify it or abandon changes. If it's valid when you exit, visudo replaces the existing sudoers with the new one.

---

### Post by ianc1 on 2011-02-16
Thanks all.  File now edited and all Ok with the password prompt every time.  Its also worked for the gksu command used when synaptic starts etc.  Which was going to be my next job.

Thanks again.

---

### Post by mc4man on 2011-02-16
If you have occasion down the road to go to natty then you'll find the sudo used now  will not allow the timestamp except on the current open instance
(so you'll have no need to edit sudoers, nor will any edit to have any effect in this regard

---

