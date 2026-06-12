---
title: "Update notifications"
date: 2011-04-28
forum: General Help
---

### Post by RobotGymnast on 2011-04-28
I installed a minimal Ubuntu, and now I don't get notified when updates are available. What package provides that functionality?

---

### Post by TeoBigusGeekus on 2011-04-28
I think it's update-notifier.

---

### Post by plucky on 2011-04-28
> **RobotGymnast said:**
> I installed a minimal Ubuntu, and now I don't get notified when updates are available. What package provides that functionality?

I think it might be

update-notifier & update-notifier-common

and is in startup applications.

Good Luck

---

### Post by RobotGymnast on 2011-04-28
> **plucky said:**
> I think it might be

update-notifier & update-notifier-common

and is in startup applications.

Good Luck

Strange, I have those, but it's not working..

---

### Post by hwttdz on 2011-04-28
You can also do ssh 127.0.0.1, and look at the header.  And you can even track down where those headers get generated and just use the command that it's using to generate the header.

---

### Post by TeoBigusGeekus on 2011-04-28
Perhaps you need a daemon or something. Try something like update-notifier-daemon.

---

