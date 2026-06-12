---
title: "Umask is broken!"
date: 2010-04-20
forum: General Help
---

### Post by the real omni on 2010-04-20
Hi,

I need to have an FTP server running where all files uploaded by users are given the permissions 775 or 765

I've tried with vsftpd and ProFTPd, setting the appropriate umask settings (tried 002 and 001) and the umask is not being applied to uploaded files with EITHER ftp daemon, so it seems to be a problem with Ubuntu.

I've also tried setting the umask to 777 just as a test. In theory any file uploaded should have 000 perms, but in every case the file that is uploaded to the server retains whatever permissions it had on the system it was uploaded from.

I have /etc/profile set to use the umask 002

Why, oh why, would Ubuntu prevent any FTP daemon from applying the umask property?? More importantly, how can I smack Ubuntu upside the head and tell it to behave properly?

Thanks!

---

### Post by the real omni on 2010-04-20
(bump)

---

