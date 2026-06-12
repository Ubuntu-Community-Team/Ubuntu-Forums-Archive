---
title: "Moving data with hardlinks to smbfs disk"
date: 2009-07-16
forum: General Help
---

### Post by megarainman on 2009-07-16
Recently I bought a Lacie 2big network drive with 3 TB of space to use for backups.  I want to use the tool backintime but I can't manage to make a backup to the new disk.  When I start the backup some folders are OK but most of them... about 95 % are empty folders. 

I mounted the lacie disk in fstab with the following command:
//192.168.0.1/share /home/lacie cifs username=xxx,password=xxx,nosuids,noperms 0 0

I can create folders, delete them, but I'm not able to make a fully working backup

I think it has something to do with the fact that the filesystem from lacie doesn't support hardlinks.  However is there a possibility to make it work?

Thanks in advance,
Kristof

---

