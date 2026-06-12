---
title: "Samba"
date: 2009-07-23
forum: General Help
---

### Post by Tsu on 2009-07-23
I have set &#8220;guest ok = yes&#8221; under a share in the samba configuration file.

I then mad the following changes

chmod -R 775 /srv/samba/share
chown -R nobody:nogroup /srv/samba/share

Yet some of the files seem to be read only.

I note that some folder will not let me save files to them. Even then the ls -l shows that the folder have the following read/write permissions.

drwxrwxr-x

I also note that some of the files have the following permissions set.

-rwxrwxr-x

Is there a guide to understanding file permission on a windows network share. As I tried turning &#8220;guest ok = no&#8221;. Then made a user account using &#8220;sudo adduser test&#8221;. Then setting &#8220;admin users = test&#8221;

[https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html](https://help.ubuntu.com/9.04/serverguide/C/samba-fileprint-security.html)

This still failed. I could not log onto the share using the user account and password I had created.

---

