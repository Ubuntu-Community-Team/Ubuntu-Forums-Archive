---
title: "Help please! how do i get administer privilege back?"
date: 2009-11-23
forum: General Help
---

### Post by blwizard on 2009-11-23
Hi guys I"m using Ubuntu 9.10 and I just unchecked the "Administer the system" from the only user that has this privilege. Now I can't use any user to make changes to system settings. Can anyone please tell me how to get the privilege back to one of my users in the system? Thanks in advance!

---

### Post by sisco311 on 2009-11-23
Reboot in *Recovery Mode* and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

---

### Post by blwizard on 2009-11-23
> **sisco311 said:**
> Reboot in *Recovery Mode* and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo]("http://psychocats.net/ubuntu/fixsudo")

Thank you so much sisco311! And that was a very quick reply! I went ahead and added a user to admin group in /etc/group without rebooting into the single user mode, and it worked right away! It's surprising that sudo was still usable, but I just couldn't do it from the graphical user interface. So can anyone explain why after I lifted the admin privilege, the user was still able to use sudo in the command line?

---

### Post by sisco311 on 2009-11-23
> **blwizard said:**
> Thank you so much sisco311! And that was a very quick reply! I went ahead and added a user to admin group in /etc/group without rebooting into the single user mode, and it worked right away! It's surprising that sudo was still usable, but I just couldn't do it from the graphical user interface. So can anyone explain why after I lifted the admin privilege, the user was still able to use sudo in the command line?

The group settings are stored in the /etc/group file.

/etc/group:
```

<groupname>:x:<groupid>:<username1>,<username2>
admin:x:115:sisco
...

```

You can add/remove a user from the a group by editing the file(not recommended, this is just an example):

```

<groupname>:x:<groupid>:<username1>,<username2>
admin:x:115:
...

```

After removing the user from the group the id command still lists the user in the group.

You have to start a new session (log out and log back in) in order the group membership to take effect. 

users-admin (Users and Groups) uses policykit to authenticate the user. 

It seams that policykit reads the /etc/group file to check if the user is in the admin group, while sudo uses a system function (like the id command) to check the membership.

So until you don't start a new login session, you can use sudo.

---

### Post by blwizard on 2009-11-24
> **sisco311 said:**
> The group settings are stored in the /etc/group file.

/etc/group:
```

<groupname>:x:<groupid>:<username1>,<username2>
admin:x:115:sisco
...

```

You can add/remove a user from the a group by editing the file(not recommended, this is just an example):

```

<groupname>:x:<groupid>:<username1>,<username2>
admin:x:115:
...

```

After removing the user from the group the id command still lists the user in the group.

You have to start a new session (log out and log back in) in order the group membership to take effect. 

users-admin (Users and Groups) uses policykit to authenticate the user. 

It seams that policykit reads the /etc/group file to check if the user is in the admin group, while sudo uses a system function (like the id command) to check the membership.

So until you don't start a new login session, you can use sudo.

That's a very good explanation. Thank you very much!

---

