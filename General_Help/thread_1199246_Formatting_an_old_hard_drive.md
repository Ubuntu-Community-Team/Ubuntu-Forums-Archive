---
title: "Formatting an old hard drive"
date: 2009-06-28
forum: General Help
---

### Post by Generic name No.8 on 2009-06-28
I have a internal hard drive that I want to start using again, but it is unable to be mounted. It shows up in Places as "56.8GB Media". So I was thinking that if I could get it formatted, it world work.

This is what shows up in basic properties

Name: 56.8 GB Media
Type: unknown type
Size: unknown
Location: computer:///
Volume: unknown
MIME type: application/octet-stream

Modified: unknown
Accessed: unknown

When trying to mount it says:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/
dev/sdb 1 ': Operation not supported Mount is denied because 
NTFS is marked to be in use. Choose one action: Choice 1: if you have windows then disconnect the external devices by        clicking on the 'Safely Remove Hardware' icon in the Windows         taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for     your own responsibility. For example type on the command line:           mount -t ntfs -3g /dev/sdb1 /media.disk -0 force          Or add the option to the relevant row in the /etc/fstab file:          /dev/sdb1/media/disk/ ntfs -3g force 0 0

When the "mount -t ntfs-3g......" is typed into the terminal it says: "only root can do that" :[

---

### Post by Saint_ on 2009-06-28
throw a sudo in front of that command; so it would be:```
 sudo mount -t ntfs-3g
``` 

Also, open up Gparted and check 56.8gb is unallocated and if that be the case you can format it to NTFS (if it's not already.)

---

### Post by Generic name No.8 on 2009-06-28
After typing "sudo.." it wanted my password, but wouldn't let me type anything else. But I have Gparted up and ready to format. Gparted says it can be formatted to :ex2 ex3 fat16 fat32 linux-swap or reiserfs. Which one should I pick?

---

### Post by Generic name No.8 on 2009-06-28
> **Saint_ said:**
> throw a sudo in front of that command; so it would be:```
 sudo mount -t ntfs-3g
```Also, open up Gparted and check 56.8gb is unallocated and if that be the case you can format it to NTFS (if it's not already.)
Replied to you btw. Don't know if it sends you a message if its just a quick reply.

---

### Post by RJ12 on 2009-06-28
> **Generic name No.8 said:**
> After typing "sudo.." it wanted my password, but wouldn't let me type anything else. But I have Gparted up and ready to format. Gparted says it can be formatted to :ex2 ex3 fat16 fat32 linux-swap or reiserfs. Which one should I pick?

Remember that when using Sudo in the terminal it dosent show your password for security reasons

---

### Post by Sef on 2009-06-28
> Gparted says it can be formatted to :ex2 ex3 fat16 fat32 linux-swap or reiserfs. Which one should I pick?

I would pick ext3 as that is the current default file system for Ubuntu.

---

