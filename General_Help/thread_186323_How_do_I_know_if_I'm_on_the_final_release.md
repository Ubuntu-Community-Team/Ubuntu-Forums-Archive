---
title: "How do I know if I'm on the final release?"
date: 2006-06-01
forum: General Help
---

### Post by tha_rainman on 2006-06-01
I've done a lot of apt-get updating but I don't have any new updates to dapper. (I have been updating quite regularly though). I've even changed my sources.list that was set to the local mirror to point to the global mirror but still no luck.

Is there a way of knowing that I'm on the final release?

*uname-r* gives the following
[I]

Linux ubuntu 2.6.15-23-amd64-k8 #1 SMP PREEMPT Tue May 23 13:51:32 UTC 2006 x86_64 GNU/Linux[/I]

---

### Post by Sgood1971 on 2006-06-01
Press ctrl+alt+F1 and in the terminal you should see Ubuntu 6.06 LTS If you have that and update manager says no updates available, then you have the latest. ctrl+alt+F7 to get back to graphical display.

---

### Post by ericesque on 2006-06-01
you could also go to System>About Ubuntu   and it will say something about Thank you for using 6.06 LTS etc.

---

### Post by tha_rainman on 2006-06-01
Well, I've been seeing that even before dapper was officially released so I was wondering if there was any other indicator...

---

### Post by tha_rainman on 2006-06-01
[QUOTE=ericesque]you could also go to System>About Ubuntu   and it will say something about Thank you for using 6.06 LTS etc.[/QUOTE]

> 
Thank you for your interest in Ubuntu 6.06 LTS
                - the Dapper Drake - released in June 2006.

Guess this is it! Thanks!

---

### Post by ericesque on 2006-06-01
heh.  I was looking for some kind of verification earlier today as well.  Unless I hear differently, updating is all it takes.

---

### Post by cjm5229 on 2006-06-02
If you run sudo apt-get dist-upgrade and have 0 updates that pretty well indicates that you are running Dapper final.
I just did a complete clean reinstall with the Final disk and I still had 1 update, I hadn't had any updates on the old install since Wed.

---

