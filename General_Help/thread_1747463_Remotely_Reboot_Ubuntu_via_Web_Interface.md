---
title: "Remotely Reboot Ubuntu via Web Interface"
date: 2011-05-02
forum: General Help
---

### Post by person287 on 2011-05-02
Is there any web interface that I can install to remotely reboot ubuntu? It would only be accessible via a VPN or on the LAN so not too much worry over security.

Thanks

---

### Post by antaios256 on 2011-05-02
> **person287 said:**
> Is there any web interface that I can install to remotely reboot ubuntu? It would only be accessible via a VPN or on the LAN so not too much worry over security.

Thanks


im no expert with ubuntu by any means but could you not enable a remote desktop through a vpn and just issue a sudo reboot comand?

---

### Post by pqwoerituytrueiwoq on 2011-05-02
you can login via ssh and run a sudo reboot command

---

### Post by cipherboy_loc on 2011-05-02
+1 SSH

While there are a few web interfaces (Webmin comes to mind), they cannot match the power of SSH.


Cipherboy

---

### Post by ~Plue on 2011-05-02
> **cipherboy_loc said:**
> 
While there are a few web interfaces (Webmin comes to mind), they cannot match the power of SSH.

edit:/ misread your post :oops:

@OP, take a look at ajaxterm if you want a web interface to use ssh

---

### Post by person287 on 2011-05-03
> **~Plue said:**
> edit:/ misread your post :oops:

@OP, take a look at ajaxterm if you want a web interface to use ssh

Ajaxterm is almost exactly what I wanted, thanks. Does anybody know though how not to bind it to localhost as I don't want to mess around with https/ssl and as it's only on the LAN it should be secure enough?
Thanks

---

