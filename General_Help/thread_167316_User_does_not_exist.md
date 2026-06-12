---
title: "User does not exist"
date: 2006-04-28
forum: General Help
---

### Post by balasatya on 2006-04-28
Hi,
I recently Installed Ubuntu Breezy Badzer 5.10  It is excellent. everything goes smoothly. But when i add a user lol and try to login with that name Ubuntu say's that " Your home directory is listed as /home/lol , but it does not appear to exit. do you like to login with root / as your home ? It is unlikely anything will work unless you use a failsafe session" ](*,) 

Could any one give me some direction ?
Thank you.

---

### Post by hw-tph on 2006-04-28
How did you add the user? If you use useradd you need to user the -m switch to create the home directory.


Håkan

---

### Post by balasatya on 2006-04-28
I have added user from GUI through system/administration/user and Groups .
Do I need to configure anything ?
Thank you :)

---

### Post by yongshunz on 2006-04-28
you can mkdir -p /home/'you id' ,

---

