---
title: "sudo -i not prompting for password"
date: 2012-06-11
forum: General Help
---

### Post by Und3rH3ll on 2012-06-11
Hi everyone.I am using ubuntu 12.04.I am facing a problem that when i use the "sudo -i" command , it is not prompting for the password.Plz help me.

---

### Post by Cheesemill on 2012-06-11
Have you used sudo recently?

You may be coming across the feature where sudo remembers your password for a set amount of time.

---

### Post by aromo on 2012-06-11
From the man pages:
>  If the invoking user is root or if the target user is the same as the invoking user, no password is required.

> Once a user has been authenticated, a timestamp is updated and the user may then use sudo without a password for a short period of time (5 minutes unless overridden in sudoers).

---

### Post by WorMzy on 2012-06-11
I you want to be prompted for a password every time you run sudo as a regular user, add "timestamp_timeout=0" to your list of Defaults by using

```
sudo visudo
```

Of course any NOPASSWD declarations will override this.

---

### Post by Und3rH3ll on 2012-06-12
sudo remember password for a set amount of time,but it is not prompting password when i am using " sudo -i" for the first time.Not even after rebooting the system.

---

### Post by agillator on 2012-06-12
As WorMzy suggested, check sudo visudo. Find the applicable entry and make sure it isn't marked for NOPASSWD. If it is, remove the NOPASSWD. If not, let us know and will look at something else.

---

### Post by Und3rH3ll on 2012-06-12
Thanks a lot.I used sudo visudo and removed the line "ALL ALL=(ALL) NOPASSWD:ALL".
Now every sudo cammand is prompting for password.Thanks again.

---

### Post by The Cog on 2012-06-12
I would worry about how that entry got there.

---

### Post by Cheesemill on 2012-06-12
> **The Cog said:**
> I would worry about how that entry got there.
+1
Unless you put that entry there yourself then your machine has been compromised in some way.

---

