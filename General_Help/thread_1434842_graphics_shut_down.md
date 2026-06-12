---
title: "graphics shut down"
date: 2010-03-20
forum: General Help
---

### Post by penn2014 on 2010-03-20
hi guys i recently posted a forum on because i had no idea how to add i second display. im pleased to say i got it added. i then tried to upgrade to karmic koala which failed because all i got was command line. i rebooted to 9.0.4 then tried it again. same result. also 10.0.4 did not work and the drivers on 9.0.4 wont activate. i seriously need help.


thanks

---

### Post by penn2014 on 2010-03-20
??!???

---

### Post by GSF1200S on 2010-03-20
What video card do you have? Can you post the contents of:
```
lspci
```
please?

When you get the command line, what does it say if you enter:
```
sudo /etc/init.d/gdm restart
```

To get graphics drivers working on 9.04 you should only need to:
```
sudo apt-get update
```
and then open the restricted drivers manager to enable the driver.

I should note that you cannot upgrade from 9.04 to 10.04. You have to upgrade to 9.10 and THEN upgrade to 10.04.

---

### Post by penn2014 on 2010-03-20
i would have to manually copy that is there a specific header im looking for for the video card

---

### Post by penn2014 on 2010-03-20
i believe the video card i had nvidia corporation nv45 [geforce 6800 gto] (rev a2)

---

### Post by penn2014 on 2010-03-20
i got 9.0.10 working

---

