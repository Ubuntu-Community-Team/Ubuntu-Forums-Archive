---
title: "Changing the username and home directory"
date: 2010-05-27
forum: General Help
---

### Post by change_mode on 2010-05-27
People usually suggest workarounds to do this, as it's not possible with usermod while the user is logged in.

Did I overlook anything or is this method not preferable over creating a new account, setting the user permissions, then moving the files and messing with the file permissions? 
Using the right tool for the job would seem to be less error-prone to me.



1. Activate the root account by setting a password.

```
sudo passwd
```

2. Log out and log into the root account.
3. Change the username and home directory from **user1** to **user2**. This will also move the files to the new home directory and rename the group to user2.

```
usermod -l user2 -d /home/user2 -m user1
```
```
groupmod -n user2 user1
```

4. Log out and log into the renamed user account.
5. Disable the root account.

```
sudo passwd -l root
```

---

### Post by Brandon Williams on 2010-05-27
You don't have to login as root to perform this operation. You do need to use a console login, since various elements of the desktop environment will stop functioning if the directories change. If you log in as user1 and run your usermod command with sudo, then immediately log out and log in as user2, you'll be OK. Just don't do anything else in the current login session after running usermod.

Note that usermod will cover you for almost everything. There is always the possibility of a config file that references that old user name though. You might want to use find to figure out whether there are any files that contain the old user name:
```
find $HOME -type f -exec grep -q user1 {} \; -print
```
Many of the listed files (if any) will need to be updated, too.

---

### Post by change_mode on 2010-05-27
> **Brandon Williams said:**
> You don't have to login as root to perform this operation. 

When I try as user1, it won't let me change anything:

```
usermod: user user1 is currently logged in
```


> Note that usermod will cover you for almost everything. There is always the possibility of a config file that references that old user name though. You might want to use find to figure out whether there are any files that contain the old user name:

Good point. I also noticed that usermod will not change the files' user group, so you'd manually have to change that from user1 to user2.

---

### Post by Brandon Williams on 2010-05-27
Huh ... I wonder when that changed. It's not a common operation, so I just had not noticed that you can no longer user 'sudo usermod' to change the name of the current user. It still works the other way on my production machine running Hardy. Looks like the slightly more involved method you describe is what's required now.

---

