---
title: "Force Log off other Users"
date: 2010-05-12
forum: General Help
---

### Post by Panik on 2010-05-12
I'm looking for a simply way to Force log off other users who may be logged into the OS.  Windows has a simple way to go into users and force log off other users.  All I have found in Ubuntu is terminal methods.  Are their no GUI tools to accomplish this?

Running Lucid 64bit

---

### Post by Panik on 2010-05-16
Nothin?  No ideas or options for this?

---

### Post by akakingess on 2010-05-16
You could look at [this]("http://software.informer.com/getfree-how-to-force-log-off-user-in-ubuntu/") although you may have already seen it, I didn't look into much myself so see what you can.

---

### Post by Oasu4g on 2010-05-16
Ultimately using the terminal to kick users will probably give you more control than a GUI.

---

### Post by r m h on 2010-05-17
man killall

i.e. sudo killall -u <username>

---

### Post by Oasu4g on 2010-05-17
How would you find out who was logged onto the system?

---

### Post by kainalu on 2010-07-20
the command w will tell you who is logged in

---

### Post by Primefalcon on 2010-07-20
> **kainalu said:**
> the command w will tell you who is logged in
who is probably easier it'll show the full username of those logged in, then you just do a killall -u <username> as stated above

---

