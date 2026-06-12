---
title: "How to add a new group created to an existing unix group"
date: 2009-08-20
forum: General Help
---

### Post by Avinash.Rao on 2009-08-20
Ubuntu 8.04 Server 64-bit Edition
Samba 3.0.28a

I have created a new group called staff and will be the primary group for 25 staff members. I tested with one user account and this user was not able to access a samba share and i found out that the user was not a member of sambashare group.

How do i add this newly created group called staff to sambashare group so that all users under staff will inherit the permissions of sambashare? 

The GUI doesn't have options for this.

Thanks
Avinash

---

### Post by nikhilk on 2009-08-20
> **Avinash.Rao said:**
> How do i add this newly created group called staff to sambashare group so that all users under staff will inherit the permissions of sambashare? 

The GUI doesn't have options for this.

I do not believe that is possible. AFAIK, only users can be added to a group, i.e. a group cannot be part of another group.

You will have to add all users from group staff to sambashare to effectively achieve what you want.

---

### Post by Avinash.Rao on 2009-08-20
Then what are the advantages of creating a new group and assigning permissions/users/groups to that group?

Tell me something, in Ubuntu when a new user account X is created, by default it creates a new group X and this becomes the primary group for this user. Now is the permissions or group memberships mapped or done for this new primary group?


Basically, i want to manage many users effectively.. 

Thanks
Avinash,



> **nikhilk said:**
> I do not believe that is possible. AFAIK, only users can be added to a group, i.e. a group cannot be part of another group.

You will have to add all users from group staff to sambashare to effectively achieve what you want.

---

### Post by Copernicus1234 on 2009-08-20
I dont think its possible either.

Its too bad really. Its more efficient to administer groups than users.

It should be easy to write a tool that on the surface makes it look like you put groups into groups, but in reality makes the necessary changes to the users instead. Not sure why someone havent.

---

### Post by Avinash.Rao on 2009-08-20
I guess this only helps to assign file or folder permissions.

---

### Post by nikhilk on 2009-08-20
> **Avinash.Rao said:**
> Then what are the advantages of creating a new group and assigning permissions/users/groups to that group?

Tell me something, in Ubuntu when a new user account X is created, by default it creates a new group X and this becomes the primary group for this user. Now is the permissions or group memberships mapped or done for this new primary group?


Basically, i want to manage many users effectively.

Yes, that is the purpose of groups. If you assign some privileges to a group instead of directly to users, it becomes easy managing adding new users or removing users via the group as opposed to doing it directly.

A user can be part of multiple groups. So I your case, if you use the group "staff" for managing something else other than just the Samba memberships, then it is still useful for users to be part of "sambashare" as well as "staff".

---

### Post by Avinash.Rao on 2009-08-20
Yeah, I got what you said. But, i still have to add these users to the group i want individually..

Thanks anyways
Avinash


> **nikhilk said:**
> Yes, that is the purpose of groups. If you assign some privileges to a group instead of directly to users, it becomes easy managing adding new users or removing users via the group as opposed to doing it directly.

A user can be part of multiple groups. So I your case, if you use the group "staff" for managing something else other than just the Samba memberships, then it is still useful for users to be part of "sambashare" as well as "staff".

---

