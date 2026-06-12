---
title: "Starting an application as an administrator using a desktop launcher"
date: 2012-07-22
forum: General Help
---

### Post by ltwinner on 2012-07-22
I am trying to launch eclipse as an administrator using a desktop launcher in ubuntu 11.04.

The name of the application is eclipse-php so the command I am using in the launcher is 

gksu "/home/me/Development/Eclipse PDT/eclipse-php"

When I double click the launcher ubuntu prompts me for a password but then nothing happens. So what's going wrong

---

### Post by ajgreeny on 2012-07-22
If that command works if you use terminal, which I assume you have tested, and the launcher itself is executable, then I have no idea why the launcher does not work.

Why not put the executable of eclipse-php in your /home/user/bin folder, which is in the system $PATH so you would need only to use gksu eclipse-php

---

### Post by ltwinner on 2012-07-23
> **ajgreeny said:**
> 
Why not put the executable of eclipse-php in your /home/user/bin folder, which is in the system $PATH so you would need only to use gksu eclipse-php

OK, I have tried putting the executable in /home/user/bin and gksu eclipse-php runs into the same issue, it asks for the admin password but doesn't load eclipse.


I have just noticed that if I go to the eclipse folder and type gksu eclipse-php it asks for the admin password then does nothing.

However if I type gksu ./eclipse-php it asks for the admin password and then loads eclipse. So what's going on here, why is that happening?

With that in mind is it possible to create a launcher for it?

---

### Post by ajgreeny on 2012-07-23
I suspect that the eclipse-php is not executable.  Right click on the file and use Properties->Permissions to set execution rights, or use terminal command ```
chmod +x */path/to/eclipse-php*
```

---

### Post by ltwinner on 2012-07-24
No the eclipse-php file has always been marked as 'Allow executing file as program'.

---

