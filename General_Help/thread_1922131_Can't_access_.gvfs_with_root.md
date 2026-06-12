---
title: "Can't access .gvfs with root"
date: 2012-02-08
forum: General Help
---

### Post by panorack on 2012-02-08
I use a ReadyNAS as storage for all my data. It is set up with two shares, one for 'media' and a second for 'backup'. 

In trying to do a backup (with sbackup) as root I discovered I cannot access the Nas box. The problem is one of permissions. Apparantly as root I do not have permision to access the '.gvfs' directory found at /home/username/.gvfs where Ubuntu mounts network storage devices.

Does anyone know why this is so since root is supposed to have access to everything, and is there a way around this?

Many thanks for any help offered.

ps. I can backup ok as user. As root I have tried both 'sudo' and 'su -' in a terminal to list the contents of .gvfs both with the same error stating lack of permission

---

