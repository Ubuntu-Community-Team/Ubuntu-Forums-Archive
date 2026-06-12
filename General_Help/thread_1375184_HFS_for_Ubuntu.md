---
title: "HFS for Ubuntu?"
date: 2010-01-07
forum: General Help
---

### Post by zac_haryy on 2010-01-07
I was just wondering if there was any sort of application that is like this one for Win [http://www.rejetto.com/hfs/](http://www.rejetto.com/hfs/) . I have an Ubuntu server running my RAID5 and love it but I was just wondering if there was something similar so that I could access files from a browser and also be able to upload files to it. I know that I could do this with an FTP client but I just wanted this for when I cant use FTP. Thanks!

-haryy

---

### Post by Leppie on 2010-01-07
this is from the rejetto page:
> It has been successfully tested with Wine under Linux.

---

### Post by Lars Noodén on 2010-01-08
@ zac_haryy : At first I thought you meant the file system used by OS X, called HFS and HFS+.  These are provided by the packages hfsplus, hfsprogs, and hfsutils.

What the link you point to might be a copy of could be WebDAV + SSL.  
You need to run WebDAV over SSL so that the login and data are encrypted.  

There are a lot of tutorials and howtos available:
[http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10](http://www.howtoforge.com/how-to-set-up-webdav-with-apache2-on-ubuntu-8.10)


However, another option, which would not use a web server at all would be to use SSHFS.

---

