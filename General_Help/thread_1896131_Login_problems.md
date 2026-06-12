---
title: "Login problems"
date: 2011-12-16
forum: General Help
---

### Post by Silentwave on 2011-12-16
Hi, i'm a oneric oncelot ubuntu user, this morning I accidentally remove the password in the administrator account and after this I cannot modify the system because if I send the empty box authentication failed.
So with this ([http://ubuntuforums.org/showthread.php?t=513820](http://ubuntuforums.org/showthread.php?t=513820)) i resolve the problem changing /etc/shadow but now the problem is that in the login screen there isn't the request of authentication with the password selected in /shadow but the password correctly work! (I can modify the system with it)
I want to put the password on login screen to enter user, how can I put things right?

Sorry for my bad english
Thanks
Silentwave :D

---

### Post by maverickaddicted on 2011-12-16
Have you check the User and Group settings? There is an option in the password section of the user "Do not ask for password on login".
Just check it.

---

### Post by Silentwave on 2011-12-16
> **maverickaddicted said:**
> Have you check the User and Group settings? There is an option in the password section of the user "Do not ask for password on login".
Just check it.
Yes I have check it and the automatic access is disabled!

---

### Post by Silentwave on 2011-12-16
up

---

### Post by Silentwave on 2011-12-16
no one can help me?

---

### Post by Silentwave on 2011-12-17
up

---

### Post by Silentwave on 2011-12-17
up

---

### Post by Silentwave on 2011-12-17
problem solved :)

---

### Post by fdrake on 2011-12-17
good for you! would you mind sharing with others?

---

### Post by Silentwave on 2011-12-17
Yes, I see that creating a new admin user the password box on login screen works, so I create a new admin user that have the "password box" at login, after this I login with this new user and delete the first admin user with option "maintaining files", after this I recreate the same user with the same Name and when i reboot pc the password box reappeared! So I login in it and delete the admin user used to solve the problem :)
All files, configurations, programs, launcher configuration in the fixed user were unchanged ;)

Sorry for my bad english
Bye

---

