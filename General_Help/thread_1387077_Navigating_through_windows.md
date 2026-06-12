---
title: "Navigating through windows"
date: 2010-01-21
forum: General Help
---

### Post by w1nst0nsm1th on 2010-01-21
Hi,

I've just installed Ubuntu 9.10 onto my netbook (toshiba nb100) from a USB key live while running xp. When I boot up I can't navigate into the windows filesystem. I assume this is because it isn't in a separate partition? How to I amend this? I want access to the windows filesystem while running ubuntu. I'd prefer not to partition. 

W1nst0n :)

---

### Post by IcarusR on 2010-01-21
On my laptop the XP partition shows as '31.5 GB Media' in the left hand pain of Nautilus. If I click on it a box asking for my password pops up, it is then mounted & visible.

---

### Post by ajgreeny on 2010-01-21
**How do I access the Windows drives?**

 The Windows partition where you installed Wubi is available as /host within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media 
 
**How can I access the Wubi files from Windows?**

 There are a few Windows applications that can mount ext2-based file systems. See for instance: 

[LIST]
[*][http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) 
[*][http://www.fs-driver.org/](http://www.fs-driver.org/) 
[/LIST]
The relevant Wubi files you need to access are located under C:\ubuntu\disks\ 
 
[B]
[/B]

---

### Post by w1nst0nsm1th on 2010-01-22
Thanks!

---

