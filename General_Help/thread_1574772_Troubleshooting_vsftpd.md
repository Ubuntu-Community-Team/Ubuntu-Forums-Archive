---
title: "Troubleshooting vsftpd"
date: 2010-09-14
forum: General Help
---

### Post by echelon-iv on 2010-09-14
I set up vsftpd to allow local users only. i then created an example user and set the home directory to where i wanted my ftp files to be. i edited the config file and uncommented the line

"write enable" 

i then restart vsftpd and tried connecting to the ftp server. i was able to connect and authenticate, but when i tried transferring any files they all failed. i get a "533 error could not create file".

any help would be much appreciated!

Thanks

echelon-iv

---

### Post by echelon-iv on 2010-09-14
i was using filezilla by the way and im running lucid lynx 

:)

---

### Post by phenym on 2010-09-17
I'm also having trouble writing files to my server. No problem getting files, just putting.

---

### Post by longvnit on 2010-09-17
You should enable the option 'write access' in /etc/vsftpd.conf

---

### Post by phenym on 2010-09-18
I had write enabled in the conf file... it still wouldn't write. So I tried writing my file to the server a different way... scp... and it still didn't work.

I tried rebooting and the problem cleared itself. Not sure what rebooting fixed.

---

