---
title: "Samba and Authorizations"
date: 2010-02-16
forum: General Help
---

### Post by pinguino99 on 2010-02-16
Hi all,
I am trying to substitute the actual file server (a win2000 server) in the Active Directory domain with a samba file server.
I managed to do many things: joining the domain, setting samba/winbind, and creating some share giving the authorizations, so i can allow some users-groups to read and/or write the share and its content.

But there is something i am still not able to do: give specific authorization to some specific files/subfolders of the share, and not just to the share.

Example, i create a share called "MyFolder", and authorizer user1 to read/write, and user2 to read only. Ok, with samba i can do it.
There is a file : MyFolder\myfile that i want to give specific authorization : read/write for user1, read/write for user2, and read ony for group group1. I cannot do this with samba.

Is it possible with samba? With a win file server i can do everything with ntfs authorizations. If i can do that also with samba, i can think to substitute the win file server.
Suggestions ?
Regards to all

---

