---
title: "Help with mounting and root access"
date: 2009-08-03
forum: General Help
---

### Post by MasaoL on 2009-08-03
I have a handful of issues i was hoping you could help me resolve.

My mother deleted Windows32 from her slave hard drive and put Vista on her master. 
Well the master was damaged and replaced we also lost the Vista boot disk.  So i installed Ubuntu. For some reason Windows shows up in the GRUB upon boot. Also it insists that the slave be run first. 

Now that problem is this. She cant mount the slave drive Ubuntu tells us that Windows is using the drive. Nor can she use the external hard drive which has no OS on it.

The last problem is she cant log in to the root. We have the password. it just insists that root cant log in on the login screen.

---

### Post by merlinus on 2009-08-03
> 
The last problem is she cant log in to the root. We have the password. it just insists that root cant log in on the login screen.
This is a built-in safeguard for linux.  Login with username and password, and you can get root access temporarily by prefacing commands with 

```
sudo  
```

or

```
gksudo
``` 

for graphical apps.

---

### Post by MasaoL on 2009-08-03
Thank you i will try that. We can access the External and slave after uping to Jaunty

---

