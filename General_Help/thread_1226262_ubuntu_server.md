---
title: "ubuntu server"
date: 2009-07-29
forum: General Help
---

### Post by robertfigl on 2009-07-29
Hi all
I have a remote ubuntu server running 8.04 with an ftp server already set-up.
The files are located in /home, where every user has the home directory just for himself and an additional directory called /ftp.

The respective /home directories are strictly for the user. No acces at all for anybody else.
The /home/ftp should be rwx for all registered users and group ftpuser. Anonymous users are not allowed at all.

All works fine, the user rights are ok and the permissions work great.

BUT:
When user A uploads a file to the ftp server, Ubuntu sets the owner and the group automatically to A A. So when user B wants to change the file it's not possible.

I want that any file uploaded by registered users, gets the rights 
Owner=User whatever / Group=ftpuser
It should be possible, that any user who is also a member of ftpuser, has rwx for all files within ftp-directory.

I hope i explained my problem well and hope for some suggestions.

Thanks a lot
Robert

---

### Post by DaithiF on 2009-07-29
Hi, what ftp package are you using on the server?  Some allow you to specify a script which runs for each uploaded file, which can be used to set the user and/or group as you wish.

---

### Post by Jago6060 on 2009-07-29
> **robertfigl said:**
> Hi all
I have a remote ubuntu server running 8.04 with an ftp server already set-up.
The files are located in /home, where every user has the home directory just for himself and an additional directory called /ftp.

The respective /home directories are strictly for the user. No acces at all for anybody else.
The /home/ftp should be rwx for all registered users and group ftpuser. Anonymous users are not allowed at all.

All works fine, the user rights are ok and the permissions work great.

BUT:
When user A uploads a file to the ftp server, Ubuntu sets the owner and the group automatically to A A. So when user B wants to change the file it's not possible.

I want that any file uploaded by registered users, gets the rights 
Owner=User whatever / Group=ftpuser
It should be possible, that any user who is also a member of ftpuser, has rwx for all files within ftp-directory.

I hope i explained my problem well and hope for some suggestions.

Thanks a lot
Robert

Did you chown the directory that the files are ftp'ed to?  Also another thought would be to look at the config for the ftp daemon, and see if you can set the permission schema in there.

---

