---
title: "Samba adding shares in smb.conf"
date: 2010-12-11
forum: General Help
---

### Post by Daniel1256 on 2010-12-11
Hi, I'm having a bit of a problem adding certain shares to my smb.conf file. I am running Ubuntu Server 10.10 and I have been asked to add the following shares:

Create a share called shared that allows read and write permissions for everyone and points to /media/shared.

Create another share called www that points to the apache web root - /var/www.
Give it read and write permissions.

So far I have:

[shared]
path = /media/share
read only = no
guest ok = yes

[www]
path = /var/www
read only = no

The first one says it should have permissions for everyone so if I set guest ok = yes that should be fine right?

Additionally I have to mount these from the desktop side which I'm not quite sure how to do. 

Now that the server is configured, the desktop needs some configuration as well. You need to mount the 2 samba partitions that reside on the server. Create a
folder called server in your home folder. In it create the &#8220;www&#8221; and &#8220;shared&#8221; folders. You need to mount the 2 shares from the server in the respective folders
on the desktop.

How can I mount these? Just ssh or something?

Thanks for helping.

---

