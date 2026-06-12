---
title: "Disable remote Login"
date: 2009-07-25
forum: General Help
---

### Post by mthalis on 2009-07-25
I want to disable remote login my computer( NO one can allow to access my machine using windows or open source software) Waiting for immediate answer

---

### Post by merlinus on 2009-07-25
System/Administration/Login Window/Remote/Disable.

---

### Post by mthalis on 2009-07-25
It is already disable 'Remote login disable' but others user can log into system.

---

### Post by mthalis on 2009-07-25
Any suggestion?

---

### Post by SlugSlug on 2009-07-25
sudo /etc/init.d/ssh stop

and then if you want it removed 
sudo apt-get remove sshd

---

