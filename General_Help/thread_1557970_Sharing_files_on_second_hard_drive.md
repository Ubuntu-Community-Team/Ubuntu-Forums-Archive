---
title: "Sharing files on second hard drive"
date: 2010-08-21
forum: General Help
---

### Post by sirfenby on 2010-08-21
Alright guys, I just installed Ubuntu and everything is going smoothly until this.
Basically I want to share the files on my second hard drive witch I use for storage over my private home network, however it just doesn't work.
I have tried sharing files from my primary hard drive with great success, but if I try to access the files from the secondary hard drive I get "Network name cannot be found" from the other compuetrs, they are running Windows 7.
Wat do?

---

### Post by sirfenby on 2010-08-21
Rescuing from page two.

---

### Post by sirfenby on 2010-08-21
Where is everyone? D:

---

### Post by Primefalcon on 2010-08-21
Are you trying to share them with Windows or Linux?

---

### Post by sirfenby on 2010-08-21
With Windows, Windows 7 to be exact.

---

### Post by Primefalcon on 2010-08-21
> **sirfenby said:**
> With Windows, Windows 7 to be exact.
that's no problems but you'll have to install samba from the software centre.... it's pretty easy to follow....

---

### Post by sirfenby on 2010-08-21
> **Primefalcon said:**
> that's no problems but you'll have to install  samba from the software center.... it's pretty easy to  follow....
Installed from software center how do I start it?

---

### Post by sirfenby on 2010-08-21
After doing some studying I have come to this, I do not have permission to access the second hard drive via network, I don't know why but Ubuntu doesn't want it to happen.
[IMG]http://img814.imageshack.us/img814/2019/screenshotqi.png[/IMG]

It dosen't seem to matter how many times I change the settings they always revert back.
I am doing this by running "gksudo nautilus" in terminal. Wat do now?

---

### Post by Morbius1 on 2010-08-21
You've created a user on Ubuntu named "administrator" ? Yikes!


Anywho, given your description of trying to change persmissons from linux and the fact that currently the permissions are set to 0700 I would conclude that the directory in question is formatted in ntfs or fat32.

Linux can't change ownership or permissions on a windows filesystem outside of a mount or in fstab.

So you have one of two options if my conclusion is correct:

Mount the partition holding the shared directory and allow access to others beside administrator. You would do that in fstab.

Or, you can use samba itself to accomplish the same affect. You would add the following line to the share definition:
```
force user = administrator
```That would act as a mask and convert the remote user ( at least for that share ) to the only local user that has access to that directory.

---

