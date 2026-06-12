---
title: "Samba server with copy/paste permission issues"
date: 2010-11-18
forum: General Help
---

### Post by the_tazinator on 2010-11-18
OK, here is my problem. I have a Ubuntu 10.04 server running samba server with multiple shares. One of those shares is a community share that all users have full access to. The client machines are a mix between Windows and Linux machines. All of the Windows machines work as expected but the issue is on Linux clients. If a file is local to the machine and then copied to the share, it retains the permissions that were set on the local machine rather than forcing the permissions set by the samba server. This usually means that only the person that copied the file to the share has access to it. The Linux users are fine if they create a new file on the share. The samba server is configure to force permissions for all new files and directories to 777 and access to those files are restricted via samba. Since this works for new files, how to I get it to apply to copy and pasted files from a Linux machine?

---

