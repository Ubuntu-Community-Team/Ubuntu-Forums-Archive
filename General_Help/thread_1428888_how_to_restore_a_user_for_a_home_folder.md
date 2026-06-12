---
title: "how to restore a user for a home folder ?"
date: 2010-03-13
forum: General Help
---

### Post by Andre-D on 2010-03-13
I messed up, and was forced to reinstall the system.
my user data ws stored on another partition  /home/Andre

I installed as a new user "test" 

How do I make a new user "Andre" such that it uses /home/Andre ?

---

### Post by sisco311 on 2010-03-13
Open a terminal & create the user:
```
sudo adduser Andre
```
Change the owner of the home directory:
```
sudo chown -R Andre: /home/Andre
```

If you want to allow the user to run programs as root, then add it to the admin group:
```
sudo gpasswd -a Andre admin
```

---

### Post by audiomick on 2010-03-13
I know you have finished the install now, but you can actually re-mount an existing /home partition during a new install. You have to choose the "manual" option at the partitioning stage of the install, select the existing /home partition to mount at /home _without formatting _, and create a user with the same user name and password as in the install in which the /home was first created.

If your install is really fresh, you might want to do it again using this method.

---

### Post by Andre-D on 2010-03-13
Thanks to you both
sisco311: your instructions worked perfectly.

Thanks.

---

### Post by Andre-D on 2010-03-19
BTW: the ported user cannot add/see printers, is asked for root password.

-any other user works fine.
-does some special permissions for CUPS need to be changed? - or what part of config do I need to delete to fix this ?

---

### Post by sisco311 on 2010-03-19
Add the user to the lp group:
```
sudo gpasswd -a **usrname** lp
```
Log out and log back in.

---

### Post by Andre-D on 2010-03-20
are you sure the group name is correct ? - (Ubuntu 10.04)
I am still getting asked for username/password, and it denies me to actually add a printer (after filling in description I cannot proceed, username is suggested as root, and my credentials are not accepted).

I have another working user, maybe I can print that user's groups-memberships and compare ?

a quick compare of [system]-[administration]-[users and groups] , Manage Groups, shows no difference between those two users..

thanks..

---

### Post by Andre-D on 2010-03-20
I see, there are big differences in "advanced settings" and "User privileges"

ok, thank you all, setting the "user privileges" solved it.

---

### Post by hman1169 on 2010-05-29
Question: If I do the install with the manual partitions and without formatting the home partition, will all the applications that were installed still be there? or do I have to re-install everything? And if after re-installing, all the settings would be pre-existing right?

---

### Post by Andre-D on 2010-05-29
> **hman1169 said:**
> Question: If I do the install with the manual partitions and without formatting the home partition, will all the applications that were installed still be there? or do I have to re-install everything? And if after re-installing, all the settings would be pre-existing right?

you'll need to make another username, I think.. or rename the old home folder before reinstalling.
and "yes", just making the installer use partition without format, will preserve data ..

---

### Post by hman1169 on 2010-05-30
Thank you! And as an update, we are going to copy his home directory to his network drive, then do a complete install... I had already done the side by side install and some other issues came up... So while talking to a Linux Guru on the phone, and logged into the friends computer in S.Korea. We discovered the partitions to be in a very strange configuration... The best and easiest result is going to be a wipe out and fresh install with a new home directory, then I will probably have to do all the permissions again when I drag his file back into the home directory... This was a suggestion of the guru! It looks to be the easiest solution.

Thanks for being there!

---

