---
title: "Samba issue: smbfs &amp; cifs = slow; kio slave smb:/ = fast ??"
date: 2006-03-11
forum: General Help
---

### Post by zi99y on 2006-03-11
Hi folks,

I've been transferring large amounts of files from a Windows XP machine to Ubuntu and thought it was a bit slow (around 1Mb/second) using a drive mounted with SMBFS in /etc/fstab. I changed this to CIFS to see if it was any better, but it was about the same.

Aha, I thought, let's try using konqueror with the SMB:/ kio slave, and now I'm getting more like 4.5-5Mb/second. This is fine but I'd like to have my mounts working this fast as I do most of my work from the shell.

Any ideas?

cheers

Here's the relevant section from my /etc/fstab (substituted "smbfs" for "cifs")
```
//totoro/c$              /media/totoro   cifs   rw,auto,user,username=xxxxx,password=xxxxxx        0       0
//totoro/storage1        /media/storage.totoro cifs     rw,auto,user,username=xxxxx,password=xxxxxx        0       0

```

---

