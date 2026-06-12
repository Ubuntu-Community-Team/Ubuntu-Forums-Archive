---
title: "User ID permissions NFS"
date: 2010-10-02
forum: General Help
---

### Post by coffee412 on 2010-10-02
I have a Fedora file server with a nfs share to a raid5 array. I noticed that Ubuntu starts off the user ids at 1000 and Redhat / Fedora systems start you out at 500. Therefore, After mounting the raid via nfs I dont have permissions. Im sure changing the user id on Ubuntu is the way to go however it is suggested that you not be logged in as that user to change the user id. So, Do I have to add another account and then login and change it or what?

Anyone else run into this or has done a user id change? Any problems ?


thanx.
:confused:

---

### Post by luvshines on 2010-10-02
You can change the UID/GID for the users by:

sudo usermod <options>

Do man usermod and you can explore the options.

But changing the ID's for local users will result in loosing the ACL's which are set on the files created by them locally.

Here is a guide to NFS on ubuntu:
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

I would suggest using NIS or LDAP server to maintain the user ID globally

---

### Post by coffee412 on 2010-10-02
> **luvshines said:**
> You can change the UID/GID for the users by:

sudo usermod <options>

Do man usermod and you can explore the options.

But changing the ID's for local users will result in loosing the ACL's which are set on the files created by them locally.

Here is a guide to NFS on ubuntu:
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

I would suggest using NIS or LDAP server to maintain the user ID globally

Thank you very much. Ill be investigating those options and Im sure one will work for me. Im going to mark this solved even though I have not done it yet. However, I will be doing it soon. 

Stupid daily question: Where do I mark it solved?

Have a great weekend!

---

### Post by luvshines on 2010-10-02
SOLVED is under the Thread Tools, first drop menu on the right just above the first post of every thread

---

