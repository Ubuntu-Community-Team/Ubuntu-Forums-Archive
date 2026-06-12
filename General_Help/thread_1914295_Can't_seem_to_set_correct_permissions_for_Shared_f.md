---
title: "Can't seem to set correct permissions for Shared file server"
date: 2012-01-24
forum: General Help
---

### Post by solarpowertoast on 2012-01-24
I have an Ubuntu 10.04 Desktop setup to share a large storage space for my wife and I.  I have 'myself' set as admin and 'wife' set as a user.  The storage space holds files such as account speadsheets, etc. that we both edit and both create new files with the intention of sharing these files with each other.  I am using samba to share the drive and have succesfully mounted the network drives on our respective laptops using by adding them to /etc/fstab

I have created a group 'family' that both 'myself' and 'wife' are in and I believe I have giving 'family' group recursive ownership of the drive.  However, when I create a file on the drive, my wife can view it, but not edit it or delete it.... and I can view hers but not edit them or delete them.  I've done some reading and a little tinkering with umask but nothing that I tried seemed to work.  At this point I have her laptop setup to access the server using 'myself' credentials, but I would prefer to have her use her own.  

Any ideas about what to try next?

---

