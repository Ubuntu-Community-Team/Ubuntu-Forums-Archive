---
title: "Users disapear"
date: 2009-08-24
forum: General Help
---

### Post by jonbjarna on 2009-08-24
I installed 9.04 about 2 weeks ago, the system ran smooth until today, all users apart from root and myself have disapeared so none of the servers (mysql apache etc) can be started.

The last thing I did was:
[https://help.ubuntu.com/community/FixShowAllUsers](https://help.ubuntu.com/community/FixShowAllUsers)
but I also installed some fixes.

Can anyone help ?

---

### Post by blueridgedog on 2009-08-24
The page you linked to is down at the moment.  Do you happen to have a backup of /etc?

---

### Post by philcamlin on 2009-08-24
> **blueridgedog said:**
> The page you linked to is down at the moment.  Do you happen to have a backup of /etc?
+1 we need dot see what you did :) but we cant without a dead link :D

---

### Post by jonbjarna on 2009-08-25
> **blueridgedog said:**
> The page you linked to is down at the moment.  Do you happen to have a backup of /etc?

I do have a backup.
This is basically the contents of the page I linked.

FixShowAllUsers 

User and Group management for system users

As default, the user configuration does not show system users. For granting group membership to e.g. apache (account www-data), you should change this: 

1. Start gconf settings editor: Alt+F2 gconf-editor Enter. 

1. In the tree, locate /apps/gnome-system-tools/users. 

1. Select the "showall" check-box. 

Now try out the user and group manager, and you should see all accounts, including computer service accounts: In the System menu, select Administration and then Users and Groups. Click on the Unlock button, and then on the Manage Groups button, and double click the group you need to manage, e.g. "subversion". You can now select the "www-data" user account to allow Apache access to subversion.

---

### Post by blueridgedog on 2009-08-25
First, determine if the users are still in /etc/passwd with:

```
cat /etc/passwd
```

Are the system accounts still there?

Are they still in /etc/shadow?

```
sudo cat /ect/shadow
```

Let's determine that they are missing for certain before we restore from a backup.

---

### Post by jonbjarna on 2009-08-25
> **blueridgedog said:**
> First, determine if the users are still in /etc/passwd with:

```
cat /etc/passwd
```

Are the system accounts still there?

Are they still in /etc/shadow?

```
sudo cat /ect/shadow
```

Let's determine that they are missing for certain before we restore from a backup.

Only root and me in both files

---

### Post by blueridgedog on 2009-08-25
Are they still in /etc/group?

As a first step, I suggest you archive your current /etc/passwd and /etc/shadow and restore your backup copy.  If you tell me where/how you are backing up, I can make a suggestion as to how.

---

### Post by jonbjarna on 2009-08-25
> **blueridgedog said:**
> Are they still in /etc/group?

As a first step, I suggest you archive your current /etc/passwd and /etc/shadow and restore your backup copy.  If you tell me where/how you are backing up, I can make a suggestion as to how.

/etc/group seems to be ok.

I did what you suggested, and my system is running now.
Thank you for sharing and for you time.

---

