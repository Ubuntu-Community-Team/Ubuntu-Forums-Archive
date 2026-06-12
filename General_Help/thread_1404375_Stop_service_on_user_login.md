---
title: "Stop service on user login"
date: 2010-02-11
forum: General Help
---

### Post by neur0 on 2010-02-11
I know this is not something that's usually done, but how do I stop a service like Apache only when I log on my user account?

---

### Post by doas777 on 2010-02-11
well, I would add an entry to your system-preferences-startup
with this as the command:

```
sudo service <servicename> stop
```
or you could do the same thing to your pre-session script.

---

### Post by neur0 on 2010-02-11
Doesn't work. Maybe its because I can't run SUDO non-interactively on log-on. Or can I ?
It doesn't make sense that any user can stop a service (which requires root privileges) by adding it to the user startup list.

I'm guessing this would be difficult to do and would involve changing the sudoers file. 

Any ideas are appreciated. I'm still trying different solutions.

---

### Post by doas777 on 2010-02-11
> **neur0 said:**
> Doesn't work. Maybe its because I can't run SUDO non-interactively on log-on. Or can I ?
It doesn't make sense that any user can stop a service (which requires root privileges) by adding it to the user startup list.

I'm guessing this would be difficult to do and would involve changing the sudoers file. 

Any ideas are appreciated. I'm still trying different solutions.


change sudo to gksu then. sorry, I shoudl have sent you that direction to start with.

---

### Post by neur0 on 2010-02-11
Ok, that works. I'm only being asked for my password after I log-on as expected. Now I only need to figure out which app to add to the sudoers file so I don't have to type my password twice when logging on. 

Thanks for the help.

---

