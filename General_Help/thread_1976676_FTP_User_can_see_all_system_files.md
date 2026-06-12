---
title: "FTP User can see all system files"
date: 2012-05-09
forum: General Help
---

### Post by HuaiDan on 2012-05-09
Greetings:

I've just set up a basic vsftp server on my Ubuntu computer at work, with "ftp" as the username (with password)that I plan on giving to my colleagues so we can share files. So far, so good.
The problem is that, simply, user "ftp" can see all my system files and directories. "Ftp" can't delete or change them in any way, except in the ftp directory, but it still makes me quite uncomfortable that anyone with this username is able to browse my system directories.
I managed to shut "ftp" out of my home directories with 
chmod 770
but how can I secure my system hard drive from browsing by "ftp" without shutting my own local user out?

Seems this should be very basic stuff, but I've found little info on it.
Thank you!

---

### Post by Peter09 on 2012-05-09
How about this
 
[http://www.linuxquestions.org/questions/linux-software-2/vsftpd-lock-user-to-home-directory-118202/](http://www.linuxquestions.org/questions/linux-software-2/vsftpd-lock-user-to-home-directory-118202/)

---

### Post by HuaiDan on 2012-05-09
Thanks, but I can't see wordpress sites or use vpn at work.
I've tried editing vsftpd.conf to read

> chroot_local_user=YES
by uncommenting that line, which has the desired result through server connection, but I'm still able to browse system files through web browser access!

---

### Post by Peter09 on 2012-05-09
Changed link in above post.

---

