---
title: "Open SSH Server - Unmet Dependancies"
date: 2006-06-07
forum: General Help
---

### Post by GTStang4793 on 2006-06-07
I am trying to install the Open SSH server on my pc so I can securely connect to it.
When I run: "sudo apt-get install openssh-server" 
I get this error: 
The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:4.1p1-7ubuntu4.1) but 1:4.2p1-7ubuntu3 is to be installed
E: Broken packages

What is wrong? How can it be fixed?

---

### Post by scxtt on 2006-06-07
could be a repository problem? (missing package perhaps) ... for me, openssh-client was installed by default, i just installed openssh-server and it worked fine ... can you check to see if openssh-client is installed, and if it isn't - install it 1st (tho this should be a problem, apt should solve dependencies) ...

is using synaptic out of the question?

---

### Post by nanotube on 2006-06-07
try using aptitude instead. it tends to be smarter about these things.
```
sudo aptitude update
sudo aptitude install openssh-server

```

---

### Post by GTStang4793 on 2006-06-08
Thank you nanotube. Using aptitude worked.

---

### Post by nanotube on 2006-06-08
[QUOTE=GTStang4793]Thank you nanotube. Using aptitude worked.[/QUOTE]
excellent. :)

---

