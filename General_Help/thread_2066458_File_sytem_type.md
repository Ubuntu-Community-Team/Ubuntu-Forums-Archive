---
title: "File sytem type"
date: 2012-10-04
forum: General Help
---

### Post by PizzaLover101 on 2012-10-04
Hope I got the title right...
When I'm at home, I use ubuntu, but my friends use windows and my school uses macs. What I am looking for is one file system type that all 3 can both read and write to.
NTFS does not work for macs.
Any help?
Thanks!

---

### Post by ezsit on 2012-10-04
FAT32 should be compatible all around. However, maximum file size is 2GB (maybe 4GB). This would only apply to very large files like video, typically.

---

### Post by bab1 on 2012-10-04
> **PizzaLover101 said:**
> Hope I got the title right...
When I'm at home, I use ubuntu, but my friends use windows and my school uses macs. What I am looking for is one file system type that all 3 can both read and write to.
NTFS does not work for macs.
Any help?
Thanks!

How are you connecting with the Macs and Windows machines?  The file system type is only relevant when mounting a partition to the local (in your case Ubuntu) file system.  Ubuntu can easily mount NTFS (Windows) EXT (Linux) and HPFS (MAC OSX), but I doubt this is what you are referring to,

If you are connecting via browsing for shares I would use Samba (CIFS).  The shares themselves should be set up to allow you to access them.  The file server sets the access not the client. 

On the default install Ubuntu is configured to see Windows shares (as the client).  Check Places>>Network or if you know where the share is located: Places>>Connect to Server and select "Windows share".  The first instance is like browsing Network Neighborhood.

---

### Post by PizzaLover101 on 2012-10-04
> **bab1 said:**
> How are you connecting with the Macs and Windows machines?  The file system type is only relevant when mounting a partition to the local (in your case Ubuntu) file system.  Ubuntu can easily mount NTFS (Windows) EXT (Linux) and HPFS (MAC OSX), but I doubt this is what you are referring to,

If you are connecting via browsing for shares I would use Samba (CIFS).  The shares themselves should be set up to allow you to access them.  The file server sets the access not the client. 

On the default install Ubuntu is configured to see Windows shares (as the client).  Check Places>>Network or if you know where the share is located: Places>>Connect to Server and select "Windows share".  The first instance is like browsing Network Neighborhood.

Oh sorry, I probably should have been more clear, I meant for a thumbdrive.

---

### Post by PizzaLover101 on 2012-10-04
> **ezsit said:**
> FAT32 should be compatible all around. However, maximum file size is 2GB (maybe 4GB). This would only apply to very large files like video, typically.

Ok, thank you!

---

