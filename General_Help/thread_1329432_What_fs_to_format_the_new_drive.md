---
title: "What fs to format the new drive?"
date: 2009-11-17
forum: General Help
---

### Post by bones12 on 2009-11-17
I have a dual boot Ubuntu 9.04 and XP desktop. I want to add a second hd to it primarily to facilitate backups, but I might as well use what's not needed for backing up.

What would be suggested as far as a file system that both OSes could read and write well. I'm getting the idea that FAT32 is the best choice but that others could work as well. And should I partition off the space for the backups?

Thanks,
Bones

---

### Post by rb0171610 on 2009-11-17
> **bones12 said:**
> I have a dual boot Ubuntu 9.04 and XP desktop. I want to add a second hd to it primarily to facilitate backups, but I might as well use what's not needed for backing up.

What would be suggested as far as a file system that both OSes could read and write well. I'm getting the idea that FAT32 is the best choice but that others could work as well. And should I partition off the space for the backups?

Thanks,
Bones
vfat

---

### Post by oldfred on 2009-11-17
You do not want FAT32. It is used for USB keys and even there it may not be the best, but is is compatible. I had a shared partition that I used for backups and they always were 4GB. So I thought I had backups, wrong. When I switched to a ext3 partition my backup was much larger. Fat has a max of 4GB and is not journalized so it is difficult to repair if it has problems.

If you want to share use NTFS. If Linux only use ext3 or ext4.

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

---

### Post by fluffman86 on 2009-11-17
I'm just posting to agree with oldfred here.  NTFS for Windows and linux sharing.  Ext4 for linux only.

---

### Post by bones12 on 2009-11-25
Thanks for the good advice. I've just received my new drive. I believe I will use NTFS since I will have to have Windoze using it.

---

