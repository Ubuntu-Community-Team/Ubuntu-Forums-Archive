---
title: "Switching user for autologin"
date: 2009-07-31
forum: General Help
---

### Post by jramos76 on 2009-07-31
I have Ubuntu installed on a machine that has autologin turned on and it logs into a locked down student account (kiosk).  Is it possible for me to switch to an administrator account (that is also on the machine) before it boots into the student account?

Any help would be appreciated. Thanks!

---

### Post by TeoBigusGeekus on 2009-07-31
System->Administration->Login Window
Go to Security tab.

---

### Post by jramos76 on 2009-07-31
I have the student account locked down to where I can't get to that menu.  Is there an alternative way?

---

### Post by jrox717 on 2009-07-31
a search returned the command
```
 gnome-session-save --kill 
```
will that work?

---

### Post by jramos76 on 2009-08-01
I don't know if that will work, but I'd like to try it.  I have the student account locked down so that a terminal can't be opened.  Is there another way to run it?

---

### Post by michy99 on 2009-08-01
Do you have a Live CD? The autologin flag is in the file /etc/gdm/gdm.conf or /etc/gdm/gdm.conf-custom.

---

### Post by jramos76 on 2009-08-03
Great!  The Live CD option worked!  Thank you all for your help! :D

---

