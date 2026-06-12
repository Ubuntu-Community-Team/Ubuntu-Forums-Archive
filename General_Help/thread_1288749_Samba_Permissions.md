---
title: "Samba Permissions"
date: 2009-10-11
forum: General Help
---

### Post by zzzBrett on 2009-10-11
Hi,

I have a samba server set up, but am having some permissions problems.  I know that unix permissions take priority over samba permissions.

When I log in as a user from a windows client to the samba server, is it that user that is accessing the file system, or is there a universal samba user that does?

I ask this because, if I set directory "Shared" to 777, I can access the directory from the client by logging in to user "A". (Directory "Shared" is owned by user "A").  But if I set the directory "Shared" to 700, I cannot access the directory.  Why is this so?  700 Should give full permissions to the owner, which is user "A", correct?

---

### Post by zzzBrett on 2009-10-11
I may have found a clue to the problem: on the client (vista), running the net use command, I can see that there are multiple connections to various shares on the server with different users. If I delete all of them, then re-login, permissions work as expected.

This may be a client issue, but is there a way to have the samba server force the client to only have one user logged into the share at a time, to prevent this from happening?

---

### Post by bryanl on 2009-10-11
The samba server has its own set of users separate from those on the system it resides in and defines the permissions of its shares by its own users. 

You can also tell samba what file permissions to set on new files in the share so you can avoid problems like you describe. The user id and password are provided when you mount the share on the client.

The client computer needs to make sure the share mount point has proper permissions for the user access, too.

---

