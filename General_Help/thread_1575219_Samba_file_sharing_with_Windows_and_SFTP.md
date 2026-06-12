---
title: "Samba file sharing with Windows and SFTP"
date: 2010-09-15
forum: General Help
---

### Post by Elan643 on 2010-09-15
Hi,

Samba newbie here.

Here's my goal:

I'm looking to set up Samba on my Ubuntu 10.04 server for file sharing with Windows PC's and to host those same shares to external users via SFTP.  I've installed Samba and I'd like to be able to have users in my company access the shares from their Windoze PC's either with or without authenticating.  There needs to be multiple folders for multiple external users that cannot see each other's data.  But, I'd like the Windows users to be able to view the root folder which contains all the users' folders so they can read/write to any of those folders.

I am able to access my folder via SFTP perfectly fine with my first Ubuntu user but how do I go about allowing the internal Windows users to access the root folders with all the shares inside of it?

Also, should I be creating new Ubuntu users for SFTP access? (I don't want them to be able to remote login via SSH).

Thanks,
Elan

---

