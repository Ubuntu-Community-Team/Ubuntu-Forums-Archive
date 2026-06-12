---
title: "Webmin, Filesystem Backup and tar files"
date: 2012-03-22
forum: General Help
---

### Post by time4e on 2012-03-22
Hello,
I have posted on the webmin [http://www.webmin.com/](http://www.webmin.com/) forums but never got a reply
I am running webmin 1.580 on FreeBSD 9. I have the Filesystem Backup module  configured to backup to a Ubuntu 11.10 box on my network over ssh, I Created a  tar file on the Ubuntu box using tar -CF archive.tar and setup Filesystem  Backup to backup to it, and the below error occurs. I am able to ssh  into the linux box without issue, how should the Tar file be setup or am  I missing something simple like using another tar program? Any ideas?


Performing backup of / to [EMAIL="tim@192.168.1.2:archive.tar"]tim@192.168.1.2:archive.tar[/EMAIL] .. 

Usage:   List:    tar -tf <archive-filename>
Extract: tar -xf <archive-filename>   
Create:  tar -cf <archive-filename> [filenames...]   Help:    tar --help  .. 

.. backup failed!

---

### Post by Habitual on 2012-03-22
Tim:

Try it as user root (in Webmin interface),

Please let us know...

---

### Post by time4e on 2012-03-22
Habitual,

Thanks for the reply. I have configured webmin to allow Unix root login and enabled all Module's for root,  and the same error occurred. After a little more testing I discovered that this may not be a Ubuntu issue. If I shutdown the Ubuntu box  and run the backup the same exact error occurs. This tells me that the issue resides on the Freebsd box and not the linux. 
Sorry :(

Thanks,
-Tim 
[]("http://ubuntuforums.org/member.php?u=504341")

---

