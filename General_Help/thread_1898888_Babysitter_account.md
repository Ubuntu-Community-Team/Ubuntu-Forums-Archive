---
title: "Babysitter account"
date: 2011-12-22
forum: General Help
---

### Post by Dragonbite on 2011-12-22
How can I create a user account that provides Internet Access for the babysitter, but does not grant her the ability to browse through user's files (let alone edit them)?

Right now I am using Ubuntu 10.04 LTS, but will likely change this April (2012).

I may or may not be home at the time, or the kids may want to use the computer while she is there, and then go to bed. So I am thinking of a login that she can use, but to keep everything else out-of-sight.

---

### Post by cybergalvez on 2011-12-22
just create a new account, by default users can't edit other users files, Also on your Documents folder you could change the access level so that "others" have no access this way they can't even be opened

---

### Post by Dragonbite on 2011-12-22
I'd prefer not having to go through and change all of the folders' permissions for all 5 family members and to enable myself to get access to them (in case of emergencies).

---

### Post by cortman on 2011-12-22
> **Dragonbite said:**
> I'd prefer not having to go through and change all of the folders' permissions for all 5 family members and to enable myself to get access to them (in case of emergencies).

Couldn't you login as the babysitter and run

```
sudo chmod u-rwx /home/other_users_folder
```

???

---

### Post by philinux on 2011-12-22
> **Dragonbite said:**
> I'd prefer not having to go through and change all of the folders' permissions for all 5 family members and to enable myself to get access to them (in case of emergencies).

IIRC you only have to do it on the main home folders. 

Yep. Scroll down for info.

 [https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

You can always get access with gksu nautilus. If need be. Not at my box so I can't test.

---

### Post by grahammechanical on 2011-12-22
I have just been testing this out to find an answer. I am using 12.04 development branch and I have two accounts. One with administrator access and one with standard access. It is true that with standard access I can access folders in the administrator home folder and read documents in them but not edit them. But ...

If, as administrator, I set the folder permissions of selected folders (such as Documents) in the administrator home folder to None (using file manager>properties>permissions>folder access others, then the standard account is not able to open the Documents folder in the administrator home folder. This works.

Be careful. Do not set the home folder itself to Others>None. When I tried that I lost the background image that I have put behind the Greeter (log in screen in 11.10 and 12.04). You will be able to do that when you get to 12.04 in April (put a background image behind the greeter, I mean).

The home folder has user configuration files that the OS needs to access. So, just change the permissions to selected folders in each user account home folder.

Regards.

P.S. as administrator you will be able to set the access level to what you need it to be if there is an emergency. See, this effort as part of your administrator privileges.

---

### Post by Derek Karpinski on 2011-12-23
He/she will really be locked down with a guest account.

Note: Ubuntu 11.10 has a guest account on the login page by default.  I assume 12.04 will too.

[http://ubuntuforums.org/showthread.php?t=1817097](http://ubuntuforums.org/showthread.php?t=1817097)

[http://ubuntuforums.org/showthread.php?t=1566078](http://ubuntuforums.org/showthread.php?t=1566078)

---

