---
title: "help with re enabling automatic login"
date: 2009-07-30
forum: General Help
---

### Post by n.hinton on 2009-07-30
I am using windows to post this as I disabled automatic login in system > administration > login window and now ubuntu will not boot past authentication failed screen how can I re enable automatic login? I can only access the ubuntu file system by booting with ubuntu CD - Please help -

---

### Post by zkriesse on 2009-07-30
What version of Ubuntu are you using?

---

### Post by n.hinton on 2009-07-30
jaunty

---

### Post by wojox on 2009-07-30
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by zkriesse on 2009-07-30
> **n.hinton said:**
> jaunty
Ok...you could probably use the repair damaged system function on the boot disk...or you could go into administration and change the password...but if you can't get in then you need to re-load the system...

---

### Post by n.hinton on 2009-07-30
> **wojox said:**
> [http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

the password is fine I need to re enable automatic login and will only be able to use Ubuntu cd unless anyone knows different

---

### Post by zkriesse on 2009-07-30
> **n.hinton said:**
> the password is fine I need to re enable automatic login and will only be able to use Ubuntu cd unless anyone knows different
Ok...then you need to go into the Administration section and re-enable it...if that don't work or if there's not an option for it then you'll have to re-load the OS...

---

### Post by n.hinton on 2009-07-30
> **Zachk18 said:**
> Ok...then you need to go into the Administration section and re-enable it...if that don't work or if there's not an option for it then you'll have to re-load the OS...

How?

---

### Post by zkriesse on 2009-07-30
> **n.hinton said:**
> How?
How what? How to reload the OS? Or how to reset the password/login...

---

### Post by n.hinton on 2009-07-30
> **Zachk18 said:**
> How what? How to reload the OS? Or how to reset the password/login...

the os can not get past the authentication failed maybe timed login to quick

---

### Post by zkriesse on 2009-07-30
> **n.hinton said:**
> the os can not get past the authentication failed maybe timed login to quick
Ok....if you CANNOT login then you need to boot from Cd by pressing F12 as soon as you turn the pc on and then reload the software altogether...do you have a different computer?

---

### Post by wojox on 2009-07-30
Editing the /etc/gdm/gdm.conf configuration file, and set AutomaticLoginEnable=true and AutomaticLogin=<username>

---

### Post by zkriesse on 2009-07-30
I think that he gave up....

---

### Post by wojox on 2009-07-30
Threw computer on ground. Jumped up & down.

---

### Post by n.hinton on 2009-07-30
> **wojox said:**
> Threw computer on ground. Jumped up & down.

Yep have just booted from CD and used gksudo gedit and edited /etc/gdm/gdm.conf-custom

back to 

AutomaticLoginEnable=true

all working again

many thanks guys

---

### Post by zkriesse on 2009-07-30
> **n.hinton said:**
> Yep have just booted from CD and used gksudo gedit and edited /etc/gdm/gdm.conf-custom

back to 

AutomaticLoginEnable=true

all working again

many thanks guys
No prob man...

---

