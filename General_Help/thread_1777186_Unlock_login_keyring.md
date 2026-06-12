---
title: "Unlock login keyring"
date: 2011-06-07
forum: General Help
---

### Post by Scunnered on 2011-06-07
Having installed Lucid I set the login screen to automatically log me in at boot.  I am however being pestered with a request :

**Enter password to unlock your login keyring**

which is not what happened in the past. I have checked and double checked but have been unable to find where I found the instruction to sort this in the past.

Can you please put me out of my misery?

---

### Post by pqwoerituytrueiwoq on 2011-06-07
to make it quit asking you can set the password on the keyring to it to null (blank/empty)
however all your password in there will be accessible to anyone using the computer

---

### Post by ajgreeny on 2011-06-07
This may be a result of your wireless trying to login and needing the keyring, so rather than delete the key as suggested by pqwoerituytrueiwoq, right click on the network-manager icon and choose "Edit Connections".  On the wireless tab highlight the wireless connection you use, and click on Edit.

Check that the two boxes top and bottom left for "**Connect automatically**" and "**Available for all users**" are both selected with a tick.  I suspect the "Available for all users" is not at the moment, hence the need for your keyring password.

---

### Post by Scunnered on 2011-06-07
My thanks to you both for your assistance. AJ hit it in the head as following his advice it worked first time.

Again my sincere thanks

---

### Post by jw1949 on 2011-06-10
I have the same problem and today had to enter the password 15-20 times (lost count).  However, when I try to edit my wireless connection it is greyed out although Connect automatically and Available to all users are both ticked.

I am finding this extremely frustrating and am tempted to go back to Maverick where I did not have this problem.   The number of times I have to enter the password does seem to be related to instances where the system has been powered off without going thro a proper shutdown ?

---

