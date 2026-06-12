---
title: "Cannot use root rights anymore! Help"
date: 2009-08-31
forum: General Help
---

### Post by BramWillemsen on 2009-08-31
Hello,

Today i booted my computer and i found out i do not have access to root anymore! When trying to use sudo i get this message "bram is not in the sudoers file.  This incident will be reported." I cannot use Synaptic anymore or any other program that requires root access.

I read some posts and people suggested using 'su' to get to root. When i do 'su root' and enter the pass i get 'authentication failure'. The way i got into this situation is probably that i did 'usermod -G pulse-rt bram'. I had some problems with pulseaudio and some guide suggested me to do this to make sure you are in the pulseaudio group. I guess this screwed up the permissions... 

How can i get access to root again as 'bram' ?
kind regards.

Bram

---

### Post by ibutho on 2009-08-31
It maybe best to use "gpasswd" to add to and remove yourself from groups instead of usermod. To sort out your problem, boot into recovery mode and then enter the command
```
gpasswd -a bram admin
```

---

### Post by P4man on 2009-08-31
boot in to recovery mode, select a root shell and run 

```
adduser your_username admin
```

---

### Post by BramWillemsen on 2009-08-31
> **ibutho said:**
> It maybe best to use "gpasswd" to add to and remove yourself from groups instead of usermod. To sort out your problem, boot into recovery mode and then enter the command
```
gpasswd -a bram admin
```

Thanks, this worked! usermod -G may have only added me to the pulse-rt group, removing the other groups i was in.

---

### Post by ibutho on 2009-08-31
> **BramWillemsen said:**
> Thanks, this worked! usermod -G may have only added me to the pulse-rt group, removing the other groups i was in.

Yes, I have had the misfortune of something similar happening to me as well. These days I just use gpasswd.

---

