---
title: "Proper shutdown check"
date: 2010-11-12
forum: General Help
---

### Post by d1brian on 2010-11-12
Is there a way to determine if Ubuntu has shutdown correctly? 

The reason I am asking this is because I want to run a virtual server using windows as host and although I can make a scheduled task that shuts down the virtual machine I don't know how to check if it serves it intended purpose. (e.g.: the host shuts down too fast and the guest doesn't shutdown properly).

Thanks in advance.

---

### Post by bioterror on 2010-11-12
> **d1brian said:**
> Is there a way to determine if Ubuntu has shutdown correctly? 

The reason I am asking this is because I want to run a virtual server using windows as host and although I can make a scheduled task that shuts down the virtual machine I don't know how to check if it serves it intended purpose. (e.g.: the host shuts down too fast and the guest doesn't shutdown properly).

Thanks in advance.

open terminal and type 'man shutdown', you get your options and it says:

> 
shutdown arranges for the system to be brought down in a safe way. All logged-in users are notified that the system is going down and,  within the last five minutes of TIME, new logins are prevented.


and 'sudo crontab -e' is your key for scheduled task.

---

### Post by d1brian on 2010-11-12
the issue is not how to shutdown the guest from inside it, but how to make the host properly shutdown the guest and to do that I need to know when the guest properly shuts down and when it doesn't.

---

