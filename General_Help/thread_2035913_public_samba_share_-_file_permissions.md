---
title: "public samba share - file permissions"
date: 2012-07-31
forum: General Help
---

### Post by Ansible on 2012-07-31
I've got an old laptop running 12.04 that I'm using as a server.  I created a samba share on it that I made public, with no security.  The idea is that anyone that gets on the network should be able to add or delete files from the share, without needing a password.  

The problem comes in with permissions.  If I'm using the laptop and I create a new file and copy it into the share, then network users don't have read permission on the file.  Similarly, if I'm on the network and I copy files to the share, the laptop user can't access those files.  

Files that are created by network users are owned by user 'nobody' and group of 'nogroup'.  Files created by the laptop user have that user as owner.  

I can fix the problem by using sudo to chown and chmod all the files in the share directory.  But as soon as I or someone else copy new files in there, the same problems arise again.

How can I set up my share so that my laptop user and network users have full read/write permissions for all files in the share without having to chown and chmod?

---

