---
title: "SMB share security"
date: 2006-03-25
forum: General Help
---

### Post by tre4 on 2006-03-25
Okay I now have ubuntu up and running fine but I really don't get how the file sharing works!!!

On windows you get sharing and then file access i.e. you may have shared a folder but that does not mean you are going to be able to access the files within the folder.....

This is not what happens with samba, or at least not with my setup it isn't.  I have files in a share with permissions only for the owner of the folder.  I'm logged into my windows machine as a different user and I kinda expected a login box to come up when I tried to access the files, but nope I went straight in!!!  I've checked security is set to user but this stilll does not seem to help.

Anyone able to give me advice.

All I want is a folder on the linux box that has files accessable by me from my computer but I want to supply a username and password every time I access that folder.

---

### Post by John.Michael.Kane on 2006-03-25
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://hr.uoregon.edu/davidrl/samba.html](http://hr.uoregon.edu/davidrl/samba.html)
[http://www.skippy.net/linux/2000/smb-howto.html](http://www.skippy.net/linux/2000/smb-howto.html)
[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html)
[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

