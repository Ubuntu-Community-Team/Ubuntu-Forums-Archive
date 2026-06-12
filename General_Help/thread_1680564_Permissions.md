---
title: "Permissions"
date: 2011-02-02
forum: General Help
---

### Post by user68 on 2011-02-02
I've installed Ubuntu server then added Gnome desktop (because I was struggling with the commands) and I've added myself as the initial user. I'm trying to add a desktop user in User Settings (Alba) and create folders in home/Alba by clicking Places > Computer > File System > Home > Alba but Create Folder is grayed out and the folder permissions say "You are not the owner, so you cannot to change permissions".

This makes no sense to me as I thought, being the initial user, I have administrator's rights and would be able to create users and folders for them.

I'm reluctant to open a GKSU Nautilus window as every time I do this, it seems to mess up my own Account Type. It changes to Custom and I lose administrator permissions. I'm really struggling with these permissions..

Should I be able to create folders for desktop users in this way?

---

### Post by sisco311 on 2011-02-02
You can use users-admin (GUI) or adduser (CLI) to create a user, set up its home directory & other settings.

Some useful links:
[uhelp]community/RootSudo[/uhelp]
[uhelp]community/AddUsersHowto[/uhelp]
[uhelp]10.04/serverguide/C/user-management.html[/uhelp]

---

### Post by user68 on 2011-02-02
Well I am using users-admin in the GUI and it does let me add a user. My problem is that after adding a new user in users-admin, I'm not able to create folders for the new user unless I log in as that user. Shouldn't I be able to add folders in home/new user as the initial user?

---

### Post by sisco311 on 2011-02-02
> **user68 said:**
> Shouldn't I be able to add folders in home/new user as the initial user?

No, by default, only the new user and root is allowed to create new files in the new user's home.

An admin user is not the same as root. Admin users are allowed to use sudo to run a command as another user or root.

---

