---
title: "Default UIDs and GIDs"
date: 2012-01-22
forum: General Help
---

### Post by StudioEngine on 2012-01-22
Hi there,

I've searched online for a while now and have not found an answer to this question.

I've joined a new Ubuntu 11.10 machine to our pre-existing AD using SSSD, which so far is working a treat.  I have however come across the following conflict.

The local user accounts on the Ubuntu box have a UID & GID which clash with existing users in the AD.  I know how to manually change the UID/GID for a local user.  But what I am after is a way to change the starting UID/GID number for future local accounts which may be created.    

I've manually changed the following options in /etc/login.defs:

UID_MIN                 20000
UID_MAX                 60000

GID_MIN                 20000
GID_MAX                 60000

However this does not seem to have any effect in newly created local accounts.

Does anyone know how to change the default sequencing of UID/GID for accounts created locally?

---

### Post by StudioEngine on 2012-01-22
So in changing the /etc/logins.defs file to the following:

UID_MIN                 20000
UID_MAX                 60000

GID_MIN                 20000
GID_MAX                 60000

You end up with this bug:

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137)

Judging by the fact that it causes the issue with the username, and does not actually set or increment the local user GID and UID, there must be some other way to manage the UID/GID sequence....

---

### Post by Krytarik on 2012-01-22
For the GUI tool "User Accounts", as well as for the command line tool "adduser" obviously, you need to change the corresponding settings in the file "/etc/adduser.conf".

"/etc/login.defs" only works for "useradd", and the other way around.

Regards.

---

### Post by StudioEngine on 2012-01-23
Thank you Krytarik, legendary!  The /etc/adduser.conf file was the one I was after..

---

