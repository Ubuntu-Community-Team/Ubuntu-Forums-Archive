---
title: "lost root password"
date: 2012-02-07
forum: General Help
---

### Post by panorack on 2012-02-07
I am running Ubuntu 11.10 and I recently needed to open a terminal as root but the password failed with an error message 'authentication failure'. Is there a way in which I can reset this or is it a complete new install? :(

Don't know if it's relevant but it is some time since I used a root terminal as opposed to using sudo and I have upgraded to 11.10 from 11.04 since then.

Many thanks for your time in reading this and any help you can offer.

---

### Post by wojox on 2012-02-07
You can reset it here [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by panorack on 2012-02-07
Tried that but got:
'passwd: authentication token manipulation error'
'passwd: password unchanged'

Tried it with my username password with same result. I did notice the drop down list in recovery mode was headed:
'Recovery Menu (limited read only menu)' 

It would seem I don't have read write permissions, which seems appropriate since anyone can boot up and select recovery and then wreak havoc.

---

### Post by CharlesA on 2012-02-07
You need to mount the file system are read/write first.

---

### Post by panorack on 2012-02-08
Many thanks for that. worked a treat. 

Still have the problem of accessing my ReadyNAS as root. Can't understand why I haven't got permission to do so, but will mark this thread as solved since my query has been resolved, and start another thread for that.

---

