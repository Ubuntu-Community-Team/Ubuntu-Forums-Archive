---
title: "Mounting C:\Users\Username\Documents to \home\username\Documents with permissions"
date: 2010-02-27
forum: General Help
---

### Post by jashale on 2010-02-27
I have a dual boot system with Ubuntu 9.10 and Windows Vista.  I want to mount the windows documents folders to my \home\username\Documents folder.  This way I am operating with only one set of documents.  I don't have to worry about sync issues.  Is this a good idea?  What should the permission look like?  Any thoughts or better ideas?

Sincerely,
Jason

---

### Post by ercferret18 on 2010-02-27
You shouldn't need to worry about permissions. They will be writable by everybody.

---

### Post by CoreyB. on 2010-02-27
@ercferret18
  Nice display pic! :D

Just auto-mount your Windows NTFS partition with ntfs-config.  Then take anything out of your Ubuntu documents folder you want and place it on your Ubuntu desktop.  Delete your Ubuntu documents folder.  Navigate to your Windows username folder that contains your Documents folder.  Left click on your Windows document folder, then in Nautilus click Edit-> Make link.  Cut the link to you ubuntu home folder, rename it Documents. Done. Enjoy.

---

