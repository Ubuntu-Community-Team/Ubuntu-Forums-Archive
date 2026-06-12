---
title: "Rsync special charset"
date: 2011-03-17
forum: General Help
---

### Post by lt-mini on 2011-03-17
hi all,

I have some issues with taking backups with rsync. Specially with filenames with special charset (éàçöü®......).

I searched for some solutions but nothing seems to work "perfect". The last thing I tried is using the "--iconv" parameter".

> Explaination backup process/
First we mount our Disk to our server (Ubuntu 10.04). Then we do rsync to a local folder called "Backup".I made some test files and tried the --iconv solution but still don't get the result i want (the original file names).
Files on the disk:
> Spéçiàlütest.txtFile in the backup folder:
> Sp__i_l_test.txt or > Spiltest.txtThe most command error in our log is also "vanished files", with the special charakters ias a "?".


USED rsync option=>  [COLOR=Navy]-vayP --iconv=ISO-8859-1,utf-8[/COLOR]
[URL="http://superuser.com/questions/183780/what-do-i-need-to-do-to-rsync-on-windows-to-make-it-keep-special-characters-in-fi"]
Website[/URL]

Kind Regards,

---

### Post by lt-mini on 2011-03-17
When i did a bit more of debugging, I see that it probably fails when i mount the drive.

When the drive is mounted i get this:
-rwxr-xr-x 1 root root   10 2011-03-17 11:37 Sp??i?l?test_ANSI.txt
-????????? ? ?    ?       ?                ? Sp??i?l?test.txt
-rwxr-xr-x 1 root root   22 2011-03-17 11:37 Sp??i?l?test_unicode_UTF16.txt
-rwxr-xr-x 1 root root   16 2011-03-17 11:36 Sp??i?l?test_UTF8.txt

After that there will be a rsync. So the problem starts with the mounting.

Is there any option in mounting four charsets?

I searched and found iocharset (in man mount) but i will search further on this.

---

### Post by lt-mini on 2011-03-18
Problem solved.

Problem was with mounting drive.


Added iocharset=utf-8 in the mount line in /etc/fstab

---

### Post by Frank DeMarco on 2011-08-02
> **lt-mini said:**
> Problem solved.

Problem was with mounting drive.


Added iocharset=utf-8 in the mount line in /etc/fstab
Many Thanks It-mini!

This problem has plagued me for weeks and I just ran across your solution.

Thanks Again 
 - Frank

---

