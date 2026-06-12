---
title: "Default keyring"
date: 2009-07-27
forum: General Help
---

### Post by rhchia on 2009-07-27
hey guys, i'm having little problem here with the default keyring when i auto login.
i've read several online help they all gave this solution.

 Install libpam-keyring
sudo aptitude install libpam-keyring

Edit the */etc/pam.d/gdm* file and add this to the last line
@include common-pamkeyring

i've my keyring and login password the same but everytime i startup, i'll still be prompt to enter the password for the keyring.

btw i'm using jaunty now.

---

### Post by lindsay7 on 2009-07-28
Go to Applications/accesories/passwords and encriptions, click on the password tab and the right click on the the password shown in the box. Type in your password and leave the other two blank. Save the hit the change button ane exit. You will get a message telling you what will happen. This should take care of your problem.

---

### Post by rhchia on 2009-07-28
> **lindsay7 said:**
> Go to Applications/accesories/passwords and encriptions, click on the password tab and the right click on the the password shown in the box. Type in your password and leave the other two blank. Save the hit the change button ane exit. You will get a message telling you what will happen. This should take care of your problem.

brilliant. thanks!

---

