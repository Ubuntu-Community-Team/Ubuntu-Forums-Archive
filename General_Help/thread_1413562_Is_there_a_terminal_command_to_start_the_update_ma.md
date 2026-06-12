---
title: "Is there a terminal command to start the update manager?"
date: 2010-02-22
forum: General Help
---

### Post by entikryst on 2010-02-22
Is there a terminal command to start the update manager?  I use fluxbox and I want to add it to my start up file but I don't know the command.

---

### Post by slakkie on 2010-02-22
Hi, please have a look at [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

---

### Post by snowpine on 2010-02-22
> **entikryst said:**
> Is there a terminal command to start the update manager?  I use fluxbox and I want to add it to my start up file but I don't know the command.

The command is: 

```
gksu update-manager
```

(this is assuming you've installed update-manager of course)

---

### Post by wojox on 2010-02-22
In the terminal you could always run:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by jfernyhough on 2010-02-22
Just

update-manager

should work, then if it needs additional permissions it will ask for an admin password (i.e. yours).

---

### Post by entikryst on 2010-02-22
Thank you all for your quick responses.

---

