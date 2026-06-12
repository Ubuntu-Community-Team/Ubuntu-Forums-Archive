---
title: "cifs share problems with desktop folder"
date: 2012-03-07
forum: General Help
---

### Post by Christopheric1 on 2012-03-07
Hey All,

I have read a few posts and have been able to configure my staff shares to map to everything from documents to pictures when they log in to the joined to AD Ubuntu machine.

The problem I run into is when I try to map the Desktop folder over to ubuntu, the desktop then fills with the icons from the $HOME directory, and I can't figure out how to change it. 

My current settings are:

-sudo apt-get install smbfs libpam-mount
 -nano /etc/pam.d/common-session
         *change pam_mount.so to come before pam_lsass.so
-sudo nano /etc/security/pam_mount.conf.xml
          *add lines <volume fstype="cifs" server="IP ADDRESS" share="share/%(DOMAIN_USER)/Desktop"
          *mountpoint="/home/likewise-open/DOMAIN/%(DOMAIN_USER)/Desktop" />

and after I do this and login to the computer the desktop has all the folders on it including documents, music, videos, etc. 

I want to know if there is a way to make it so the Desktop Folder maps correctly. 

Thanks for all your help!

---

