---
title: "How to grant read access to flash drive"
date: 2012-07-08
forum: General Help
---

### Post by susja on 2012-07-08
Hello,
I'm using Plex Media Server and provide path to Videos folder to scan. Now I started to use flash drive as well and added the path to flash drive to scan as well. I realized that it failed to scan flash. Log shows this error:
Jul 08, 2012 20:27:29 [0xb7750700] DEBUG - Scanning USB with 0 current items in the database...
Jul 08, 2012 20:27:29 [0xb7750700] DEBUG - Performing a scan with 'Plex Movie Scanner' (language: en virtual: 0).
Jul 08, 2012 20:27:29 [0xb7750700] DEBUG -   * Scanning /media/62744BA250E521E0
Jul 08, 2012 20:27:29 [0xb7750700] WARN - Caught exception while scanning USB: boost::filesystem::directory_iterator::construct: Permission denied: "/media/62744BA250E521E0"
The user running Plex is plex:
# id plex
uid=115(plex) gid=127(plex) groups=127(plex)
Permission on flash:
eliya@Linda:/media/62744BA250E521E0$ ls -ld .
drwx------ 1 eliya eliya 4096 Jul  8 10:46 .
I added user 'plex' to group 'eliya' but I can't modify group access for flash using chmod
I tried to share flash drive but it didn't help me.
My question: how could I grant user 'plex' access to scan /media/62744BA250E521E0 ?
Thanks


P.S.
 I realized that I have NTFS on my flash. I reformatted it to ext3 and was able modify all permission that I needed. But the problem is that my TV box ( which I'm going to use with this flash ) does not support NTFS ( only FAT 32 and NTFS ). Well I had to reformat again to NTFS and hit the wall. Neither owner (eliya) nor root could modify anything on this flash drive?
Any ideas how to work around it?
Thanks

---

### Post by susja on 2012-07-15
I resolved the issue myself by modifying /etc/fstab file.
Thanks

---

