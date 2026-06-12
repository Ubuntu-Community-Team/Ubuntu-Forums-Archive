---
title: "Need some things cleared up!"
date: 2006-01-27
forum: General Help
---

### Post by anths on 2006-01-27
Ok, these questions have been answered before, many times over... and that is what is confusing me. If I want to share files over SMB, where should I have them mounted on the server? Currently they are in /home/*username* but I am not sure if this is correct. Secondly, I need to know how to then mount said file share on the client computer using stab. smbmount or do I mount it like a regular drive using smbfs for the file system type (an example line would help A TON here guys!) 

Thanks so much

---

### Post by uberlaff on 2006-01-27
Hey... I think I can answer this question for you.  Try loading all the files you want to share into a single directory.  Then right click on that folder and in the menu you can select share folder.  This should allow you to share the folder on the network and give any windows machine access to it. 

Let me know if that works...

---

### Post by hw-tph on 2006-01-27
For non-personal shares I usually create a /usr/local/smbshare directory and set up the permissions so that members of a certain group have write access to the directory. I add a corresponding share section in /etc/samba/smb.conf and restart Samba. That's all there is to it. There are plenty of guides on the web.

Oh, and the same shared directory is also exported using NFS.


Håkan

---

