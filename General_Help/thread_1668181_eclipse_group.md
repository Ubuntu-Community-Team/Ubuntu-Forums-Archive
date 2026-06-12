---
title: "eclipse group"
date: 2011-01-16
forum: General Help
---

### Post by anjanesh on 2011-01-16
I've installed eclipse and android manually at /opt.
How do I make /opt/android writable by eclipse ? I don't want to chmod it to 777.
Specifically I need to know the group eclipse belongs to.

---

### Post by noah++ on 2011-01-16
I am not sure whether it's the application's group ID or the user's that's effective here. Anyway, to find out Eclipse's group, just do an **ls -l /opt/eclipse**, replacing */opt/eclipse* with the right path to the Eclipse binary if that's not it.

---

### Post by GregBrannon on 2011-01-16
Did you have to install Eclipse at that location?  Rather than futz around with system permissions, why not just install Eclipse to a folder off your home directory?  Eclipse doesn't care where it is, and it would make your programming environment much simpler and easier to manage.

---

### Post by anjanesh on 2011-01-16
Yes. Eclipse is at /opt/eclipse and android at /opt/android
> Rather than futz around with system permissions, why not just install Eclipse to a folder off your home directory?
Im syncing /home/*username* to my S3 account. I want /home/username to be only data and not programs.

For now I got it writable by my *username*, but I would prefer it writable by the group like www-data for apache. But since this is a desktop, I guess this is ok ?
sudo chgrp -R *username* android/
chmod -R g+w android/

---

