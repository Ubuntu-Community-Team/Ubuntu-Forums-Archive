---
title: "ftp 553 error"
date: 2010-01-30
forum: General Help
---

### Post by cop01 on 2010-01-30
I have setup a ubuntu webserver (server edition) and loaded vsftpd on as a ftp server so I can upload files to it.
 
I am using filezilla as my ftp client and I can upload new files to the directory on the ubuntu webserver without a problem. However if I change a file and then try and upload it, it asks me if I want to overwrite the existing file. When I say yes it gives me the ftp 553 error can create file.
 
I created an ftp user (wandb) and their home directory is the /var/www/weightb directory
 
The permissions are below:
 
drwxrwxrwx 3 wandb wandb 4096 2010-01-23 15:26 weightb
 
Any idea where I am going wrong?

---

