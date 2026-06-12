---
title: "Error running downloads"
date: 2011-08-12
forum: General Help
---

### Post by BlackEmpire77 on 2011-08-12
I downloaded Cyberghost VPN,on Ubuntu 11.04, now everytime I try to run it I get this.        There was an error launching the application. Details: Failed to change to directory '/home/marki/.wine/dosdevices/c:/Program Files/S.A.D/CyberGhost VPN' (No such file or directory). Can anyone help me get this running.

---

### Post by aeiah on 2011-08-12
does the file exist at that location? on the properties of the launcher/menu item/whatever-you're-clicking, is the path encapsulated by quotes? if not, try doing that, or try replacing each space with a backslash and a space, as such:

/home/marki/.wine/dosdevices/c:/Program\ Files/S.A.D/CyberGhost\ VPN

---

