---
title: "File Permissions"
date: 2010-09-25
forum: General Help
---

### Post by rensell on 2010-09-25
Hi all, I've got an irritating issue today. I've got Ubuntu Server 10.04 up and running. Among other things, it runs samba and share a 1TB drive across my network. I have 1 share for the entire drive - /mnt/iomega shared as iomega. I have a folder /mnt/iomega/mydocs/ray/dell/drivers that I have access denied to everyone except me - when I enter my username and password from client (windows) everyone else says access is denied.

Today, I booting the server to my old XP install to run some other programs that I'm still trying to find Linux replacements for, anyhow I enable "other users to change my files" on my iomega share from XP and now everyone can access my dell/drivers folder. I've tried chown and everything - it says it's completed but it doesn't change anything. ls -l shows that root root is the owner of all my mounted drives now and I can't get anything to change back.

Any ideas?

Thanks,
-R

---

### Post by roccivic on 2010-09-25
is it an ext filesystem (ext2, ext3, ext4) that you share? If not, then chown/chmod won't help you.

---

### Post by bodhi.zazen on 2010-09-25
If it is a FAT or NTFS partition you set ownership and permissions at the time of mount, see:

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

