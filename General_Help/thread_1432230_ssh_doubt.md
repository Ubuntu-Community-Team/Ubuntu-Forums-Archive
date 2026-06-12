---
title: "ssh doubt"
date: 2010-03-17
forum: General Help
---

### Post by jsriz on 2010-03-17
Our Lab at college has basically many ubuntu systems connected in a  network.
now just for fun we ssh into some random systems and close all running  programs so on....
i would like to know how to disconnect these ssh connections which show  up when i do 
"finger"

---

### Post by sideburns on 2010-03-17
If you want to stop other students from playing this game with your box once and for all, simply close Port 22 in your firewall.

---

### Post by jsriz on 2010-03-17
> **sideburns said:**
> If you want to stop other students from playing this game with your box once and for all, simply close Port 22 in your firewall.
please could you tell me how to do it....................

---

### Post by Dougie187 on 2010-03-17
you could always turn off sshd.

```
sudo service sshd stop
```

though this will make it so NOONE (not even you) can ssh into it. But thats also what closing port 22 will do.

---

### Post by spiky001 on 2010-03-17
You could change the port no is an option

---

### Post by prodigy_ on 2010-03-17
If you just want to achieve a reasonable level of security but don't want to turn sshd off completely:

Change the sshd port from 22 to something else and disable all authentication methods except DSA key/diffie-hellman exchange. Also create only passphrase-protected keys for clients.

---

### Post by cariboo on 2010-03-17
As with your other thread. This one is closed.

---

