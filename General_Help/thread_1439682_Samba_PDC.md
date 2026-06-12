---
title: "Samba PDC"
date: 2010-03-26
forum: General Help
---

### Post by david90 on 2010-03-26
When my samba PDC is off, why computers in the domain still able to log in?

---

### Post by david90 on 2010-03-27
Anybody?  The machines in the domain could still log on but get the message profile not found.  If the PDC is off, I would expect windows to denied log in since it can't authenticate with the PDC.

---

### Post by david90 on 2010-03-28
bump

---

### Post by wrp on 2010-05-05
This is your Windows workstation. 
I think you will find that your authentication details are being "remembered" by the local workstation and it checks the username and password supplied against this information. 
Of course this will only work if you (the user) have previously been authenticated by the PDC on that workstation. 
I am sure there is a way of turning off this "feature" but you will need to consult the Microsoft support site for this information. 
Its actually quite helpful if a laptop is taken offsite etc.

---

