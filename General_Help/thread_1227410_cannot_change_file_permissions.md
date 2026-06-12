---
title: "cannot change file permissions"
date: 2009-07-30
forum: General Help
---

### Post by sdlynx on 2009-07-30
I am trying to change a folder (/windows) so that I am the owner, at the moment it is root, but the permissions won't change.  I ran 'sudo nautilus', and tried to change the permissions but when I chose my username instead of root for the owner it just changed back, same for trying to change anything else.... I also tried 'chown username:username /windows -Rhv', and it shows that it is changing each file, but when I try to change anything or check the permissions haven't changed.  Help?

---

### Post by michy99 on 2009-07-30
Is this a separate partiton with your Windows system on it? If so it will either be NTFS or FAT32. Permissions on these filesystems are set at the time they are mounted.

---

### Post by sdlynx on 2009-07-30
ah, yes it is, thanks

I'll fix that and see what happens

---

